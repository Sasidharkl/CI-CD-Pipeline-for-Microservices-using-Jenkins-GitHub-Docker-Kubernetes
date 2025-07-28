pipeline {
  agent any

  environment {
    IMAGE_NAME = "yourdockerhubusername/myapp"
    TAG = "${BUILD_NUMBER}"
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/yourusername/your-repo.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Docker Build & Push') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
            def app = docker.build("${IMAGE_NAME}:${TAG}")
            app.push()
          }
        }
      }
    }

    stage('Deploy to K8s') {
      steps {
        sh '''
          kubectl set image deployment/myapp-deployment myapp=${IMAGE_NAME}:${TAG}
        '''
      }
    }
  }

  post {
    success {
      slackSend channel: '#ci-cd', message: \"✅ Build #${BUILD_NUMBER} deployed successfully.\"
    }
    failure {
      slackSend channel: '#ci-cd', message: \"❌ Build #${BUILD_NUMBER} failed.\"
    }
  }
}

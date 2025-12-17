pipeline {
  agent any

  environment {
    IMAGE_NAME = "ahmaddocknroll/weather-app"
    IMAGE_TAG  = "${env.BUILD_NUMBER}"
    APP_PORT   = "5000"   
  }


  stages {

    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker image') {
      steps {
        sh '''
          docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
        '''
      }
    }

    stage('Push image to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
          sh '''
            echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
            docker push ${IMAGE_NAME}:${IMAGE_TAG}
          '''
        
        }
      }
    }

    stage('Deploy with Docker Compose') {
      steps {
        withCredentials([string(credentialsId: 'openweather-api-key', variable: 'API_KEY')]){
        sh '''
          export IMAGE_NAME=${IMAGE_NAME}
          export IMAGE_TAG=${IMAGE_TAG}
          export API_KEY=${API_KEY}
          docker compose down
          docker compose up -d
        '''
        }
      }
    }
  }

  post {
    success {
      echo " App deployed successfully at port ${APP_PORT}"
    }
    failure {
      echo " Deployment failed. Check logs for details."
    }
  }
}

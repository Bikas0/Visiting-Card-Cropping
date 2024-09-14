pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS='dockerhub'
        DOCKER_IMAGE_NAME = "bikas0/card_cropping"
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Hello') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'githubtoken', url: 'https://github.com/Bikas0/Visiting-Card-Cropping.git']])
            }
        }

        stage('Build Docker Image'){
            steps{
                script{
                    echo 'Building Docker Image...'
                    sh """
                    docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_TAG} .
                    """
                }
            }
        }
    }
  stage('Login to Docker Hub') {
      steps {
          script {
              echo 'Logging into Docker Hub...'
              // Log in to Docker Hub using credentials stored in Jenkins
              withCredentials([usernamePassword(credentialsId: DOCKER_HUB_CREDENTIALS, passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                  sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
              }
          }
      }
  }
  stage('Push Docker Image to Docker Hub') {
      steps {
          script {
              echo 'Pushing Docker image to Docker Hub...'
              // Push the Docker image to Docker Hub (optional)
              sh """
              docker push ${DOCKER_IMAGE_NAME}:${DOCKER_TAG}
              """
          }
      }
  }
  stage('Deploy Docker Container in Detached Mode') {
        steps {
            script {
                echo 'Deploying Docker container in detached mode...'
                // Stop the container if it's already running
                // sh """
                // docker stop your-app-container || true
                // docker rm your-app-container || true
                // """
                // Run the container in detached mode
                sh """
                docker run -d --name visiting_card -p 8005:8005 ${DOCKER_IMAGE_NAME}:${DOCKER_TAG}
                """
            }
        }
    }
}

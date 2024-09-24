pipeline {
    agent any // IN THE LECTURE I WILL EXPLAIN THE SCRIPT AND THE WORKFLOW

    environment {
        // Define Docker Hub credentials ID
        DOCKERHUB_CREDENTIALS_ID = 'yahhas'
        // Define Docker Hub repository name
        DOCKERHUB_REPO = 'yahhas/tempconverter'
        // Define Docker image tag
        DOCKER_IMAGE_TAG = 'latest'
    }

    tools {
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git 'https://github.com/Mihuy1/TemperatureTestJenkins'
            }
        }
        stage('Build Docker Image') {
            steps {
                // Build Docker image
                script {
                    docker.build("${DOCKERHUB_REPO}:${DOCKER_IMAGE_TAG}")
                }
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                // Push Docker image to Docker Hub
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKERHUB_CREDENTIALS_ID) {
                        docker.image("${DOCKERHUB_REPO}:${DOCKER_IMAGE_TAG}").push()
                    }
                }
            }
        }
    }
}
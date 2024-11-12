
pipeline {
    agent any

    environment {
        // Docker image name and registry details
        DOCKER_IMAGE_NAME = 'christalselvin/pypsrp'
        DOCKER_REGISTRY = 'https://hub.docker.com'
    }

    stages {
        // Stage 1: Clone the GitHub repository
        stage('Clone Repository') {
            steps {
                git 'https://github.com/christalselvin/Pypsrp-Paramiko.git'
            }
        }

        // Stage 2: Build the Docker image
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image using the Dockerfile in your project
                    docker.build(DOCKER_IMAGE_NAME)
                }
            }
        }

        // Stage 3: Publish the Docker image to Docker Hub
        stage('Publish Docker Image') {
            steps {
                script {
                    // Log in to Docker Hub and push the image
                    docker.withRegistry('https://docker.io', 'dockerhub-access-token') {
                        docker.image(DOCKER_IMAGE_NAME).push('latest')
                    }
                }
            }
        }
    }
}

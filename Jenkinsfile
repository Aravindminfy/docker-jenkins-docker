pipeline {
    agent any

    environment {
        IMAGE_NAME = "aravind399/python-demo-app"
        DOCKER_USERNAME = "aravind399"
        DOCKER_PASSWORD = "************" 
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning the repository...'
            
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Login to Docker Hub') {
            steps {
                echo 'Logging in to Docker Hub...'
                sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
            }
        }

        stage('Push Docker Image to Hub') {
            steps {
                echo 'Pushing image to Docker Hub...'
                sh "docker push $IMAGE_NAME"
            }
        }

        stage('Pull Docker Image from Hub') {
            steps {
                echo 'Pulling image from Docker Hub (fresh)...'
                sh "docker pull $IMAGE_NAME"
            }
        }

        stage('Run Docker Container') {
            steps {
                echo 'Running Docker container...'
                sh "docker run --rm $IMAGE_NAME"
            }
        }
    }
}

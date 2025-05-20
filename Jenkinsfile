pipeline {
    agent any

    environment {
        IMAGE_NAME = "aravind399/python-demo-app"
        DOCKER_USERNAME = "aravind399"
        DOCKER_PASSWORD = "Ai@304491" // ⚠️ Replace with **** if sharing publicly
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning the repository...'
                // You can add `git 'https://github.com/user/repo.git'` here
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

        stage('Run Docker Container') {
            steps {
                echo 'Running Docker container...'
                sh "docker run --rm $IMAGE_NAME"
            }
        }
    }
}

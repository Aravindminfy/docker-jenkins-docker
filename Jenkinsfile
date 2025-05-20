pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo 'Cloning the repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run --rm python-demo-app'
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t "your-docker-image:latest" .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 5000:80 your-docker-image:latest'
            }
        }
    }
}


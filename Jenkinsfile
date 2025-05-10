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
                // Expose container port 80 to host port 8080
                bat 'docker run -d -p 8000:80 your-docker-image:latest'
            }
        }
    }
}

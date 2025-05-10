
          

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
                bat 'docker run -d your-docker-image:latest'
            }
        }
    }
}

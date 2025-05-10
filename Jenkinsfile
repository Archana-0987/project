pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "your-docker-image"  // Your Docker image name
        DOCKER_TAG = "latest"  // Tag for the image
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/Archana-0987/project.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.run("${DOCKER_IMAGE}:${DOCKER_TAG}", "-d")
                }
            }
        }

        stage('Post-Build Actions') {
            steps {
                echo 'Docker container is now running'
            }
        }
    }

    post {
        always {
            // Cleanup after the build
            sh 'docker ps -a'
            sh 'docker stop $(docker ps -aq)'
            sh 'docker rm $(docker ps -aq)'
        }
    }
}

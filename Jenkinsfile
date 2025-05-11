pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = "1ds23cs403"
        DOCKER_HUB_IMAGE = "your-docker-image"
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Use SSH for GitHub cloning (Windows may require additional setup for SSH)
                bat 'git clone git@github.com:your-username/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image (use bat instead of sh for Windows)
                    echo "Building Docker image..."
                    bat "docker build -t ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to Docker Hub (use bat instead of sh for Windows)
                    echo "Pushing Docker image to Docker Hub..."
                    bat "docker push ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Apply the Kubernetes deployment file (use bat instead of sh for Windows)
                    echo "Deploying to Minikube Kubernetes..."
                    bat "kubectl apply -f deployment.yaml"
                }
            }
        }
    }
}

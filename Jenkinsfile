pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = "1ds23cs403"
        DOCKER_HUB_IMAGE = "your-docker-image"
        GITHUB_REPO = "https://github.com/Archana-0987/project.git"
        GITHUB_CREDENTIALS = 'github-jenkins-token'  // This is the Jenkins credential ID for GitHub token
    }

    stages {
        stage('Checkout') {
            steps {
                // Use Jenkins Git plugin for cloning the repository
                git credentialsId: "${GITHUB_CREDENTIALS}", url: "${GITHUB_REPO}"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    echo "Building Docker image..."
                    bat "docker build -t ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to Docker Hub
                    echo "Pushing Docker image to Docker Hub..."
                    bat "docker push ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Apply the Kubernetes deployment file
                    echo "Deploying to Minikube Kubernetes..."
                    bat "kubectl apply -f deployment.yaml"
                }
            }
        }
    }
}

              
                  

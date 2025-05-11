pipeline {
    agent any

    environment {
        DOCKER_HUB_USERNAME = "1ds23cs403"
        DOCKER_HUB_IMAGE = "your-docker-image"
        KUBECONFIG = "C:\\Users\\HP\\.kube\\config" // Make sure this path is correct
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone your GitHub repository containing the Dockerfile
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    echo "Building Docker image..."
                    sh "docker build -t ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Log in to Docker Hub and push the Docker image
                    echo "Pushing Docker image to Docker Hub..."
                    sh "docker push ${DOCKER_HUB_USERNAME}/${DOCKER_HUB_IMAGE}:latest"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Apply the Kubernetes deployment file to Minikube
                    echo "Deploying to Minikube Kubernetes..."
                    sh "kubectl apply -f deployment.yaml"
                }
            }
        }
    }
}


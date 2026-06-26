pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = "341796273562"
        AWS_REGION = "us-east-1"
        ECR_REGISTRY = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Login to ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region $AWS_REGION | \
                docker login --username AWS --password-stdin $ECR_REGISTRY
                '''
            }
        }

        stage('Build Docker Images') {
            steps {
                sh '''
                docker build -t streaming-frontend ./frontend
                docker build -t streaming-auth ./backend/authService
                docker build -t streaming-admin ./backend/adminService
                docker build -t streaming-chat ./backend/chatService
                docker build -t streaming-streaming ./backend/streamingService
                '''
            }
        }

        stage('Tag Images') {
            steps {
                sh '''
                docker tag streaming-frontend:latest $ECR_REGISTRY/streaming-frontend:latest
                docker tag streaming-auth:latest $ECR_REGISTRY/streaming-auth:latest
                docker tag streaming-admin:latest $ECR_REGISTRY/streaming-admin:latest
                docker tag streaming-chat:latest $ECR_REGISTRY/streaming-chat:latest
                docker tag streaming-streaming:latest $ECR_REGISTRY/streaming-streaming:latest
                '''
            }
        }

        stage('Push Images') {
            steps {
                sh '''
                docker push $ECR_REGISTRY/streaming-frontend:latest
                docker push $ECR_REGISTRY/streaming-auth:latest
                docker push $ECR_REGISTRY/streaming-admin:latest
                docker push $ECR_REGISTRY/streaming-chat:latest
                docker push $ECR_REGISTRY/streaming-streaming:latest
                '''
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                helm upgrade --install streaming-app ./helm -n streaming-app
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                kubectl get pods -n streaming-app
                kubectl get svc -n streaming-app
                '''
            }
        }
    }
}
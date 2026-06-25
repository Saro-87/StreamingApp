pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = "341796273562"
        AWS_REGION = "us-east-1"
    }

    stages {

        stage('Git Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend') {
            steps {
                sh 'docker build -t streamingapp-frontend ./frontend'
            }
        }

        stage('Build Auth') {
            steps {
                sh 'docker build -t streamingapp-auth ./backend/authService'
            }
        }

        stage('Build Admin') {
            steps {
                sh 'docker build -t streamingapp-admin ./backend/adminService'
            }
        }

        stage('Build Chat') {
            steps {
                sh 'docker build -t streamingapp-chat ./backend/chatService'
            }
        }

        stage('Build Streaming') {
            steps {
                sh 'docker build -t streamingapp-streaming ./backend/streamingService'
            }
        }
    }
}
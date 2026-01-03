pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/sonugupta4166/portfilio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                echo "Building Docker image..."
                docker build -t portfolio:v1 .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                echo "Stopping old container (if exists)..."
                docker stop portfolio || true
                docker rm portfolio || true

                echo "Starting new container..."
                docker run -d -p 80:80 --name portfolio portfolio:v1
                '''
            }
        }
    }
}

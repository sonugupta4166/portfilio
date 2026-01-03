pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/sonugupta4166/portfilio.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t portfolio:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop portfolio || true
                docker rm portfolio || true
                docker run -d -p 80:80 --name portfolio portfolio:v1
                '''
            }
        }
    }
}

pipeline {
    agent any

    environment {
        IMAGE_NAME = "sathvikdandey/node-docker-app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sathvik-dande/new_practice.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME:${BUILD_NUMBER} .
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f node-app || true
                docker run -d --name node-app -p 3001:3000 $IMAGE_NAME:${BUILD_NUMBER}
                '''
            }
        }
    }
}

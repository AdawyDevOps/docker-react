pipeline {
    agent { label 'docker' }

    stages {
        stage('Checkout code') {
            steps {
                // هيتأكد إن Git يسحب الكود من المشروع
                checkout scm
            }
        }

        stage('Build Docker image') {
            steps {
                // غيّر المجلد للـ project path
                dir('/home/adawy/react-project') {
                    sh 'docker build -t adawy123/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run tests') {
            steps {
                dir('/home/adawy/react-project') {
                    sh 'docker run -e CI=true adawy123/docker-react npm run test'
                }
            }
        }
    }
}

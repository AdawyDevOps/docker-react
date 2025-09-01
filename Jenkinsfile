pipeline {
    agent { label 'docker' }

    stages {

        stage('Checkout code') {
            steps {
                // نسحب الكود من GitHub
                checkout scm
            }
        }

        stage('Build Docker image') {
            steps {
                // نستخدم نفس مجلد workspace كـ context للـ Docker
                dir("${env.WORKSPACE}") {
                    sh 'docker build -t adawy123/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run tests') {
            steps {
                dir("${env.WORKSPACE}") {
                    sh 'docker run -e CI=true adawy123/docker-react npm run test'
                }
            }
        }
    }
}

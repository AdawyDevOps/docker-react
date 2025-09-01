pipeline {
    agent { label 'docker' }

    stages {
        stage('Checkout code') {
            steps {
                // يجيب الكود من Git
                checkout scm
            }
        }

        stage('Build Docker image') {
            steps {
                // يبني الصورة من نفس الـ workspace
                sh 'docker build -t adawy123/docker-react -f Dockerfile.dev .'
            }
        }

        stage('Run tests') {
            steps {
                // يشغل حاوية Docker ويشغل الاختبارات
                sh 'docker run -e CI=true adawy123/docker-react npm run test'
            }
        }
    }
}

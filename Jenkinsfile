pipeline {
    agent { label 'docker' }

    stages {

        stage('Checkout code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    sh 'docker build -t adawy123/docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Run tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = 1
                    sh 'docker run -e CI=true adawy123/docker-react npm run test'
                }
            }
        }

        stage('Debug Workspace') { 
            steps {
                sh 'ls -la'
            }
        }
    }
}

}
 
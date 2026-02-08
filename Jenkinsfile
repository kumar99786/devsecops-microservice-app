pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-creds',
                    url: 'https://github.com/kumar99786/devsecops-microservice-app.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'docker build -t backend-app -f Dockerfile.backend .'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t frontend-app -f Dockerfile.frontend .'
            }
        }

        stage('List Docker Images') {
            steps {
                sh 'docker images'
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully'
        }
        failure {
            echo 'CI pipeline failed'
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker compose -p devops-app build'
            }
        }

        stage('Docker Deploy') {
            steps {
                sh 'docker compose -p devops-app down || true'
                sh 'docker compose -p devops-app up -d'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker compose -p devops-app ps'
            }
        }
    }
}

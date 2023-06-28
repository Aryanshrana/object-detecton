pipeline {
    agent any

    stages {
        stage('Authentication') {
            steps {
                sh 'cd yolo5...'
            }
        }
        stage('Build') {
            steps {
                sh 'echo building...'
            }
        }
        stage('Push to ECR') {
            steps {
                sh 'echo pushing...'
            }
        }
    }
}
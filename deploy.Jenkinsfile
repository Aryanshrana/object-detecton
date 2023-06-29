pipeline {
    agent any

    parameters { string(name: 'YOLO5_IMAGE_URL', defaultValue: '', description: '') }

    stages {
        stage('Deploy in k8s') {
            steps {

                sh '''
                    echo authenticate
                    kubectl apply -f yolo5-deployment.yaml
                '''
            }
        }
    }
}
pipeline {
    agent any

    parameters { string(name: 'YOLO5_IMAGE_URL', defaultValue: '', description: '') }

    stages {
        stage('Setting default namespace') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                    sh 'kubectl config set-context --current --namespace=${aryansh-ns}'
                }
            }
        }
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
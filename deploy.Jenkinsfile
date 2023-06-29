pipeline {
    agent any

    parameters { string(name: 'YOLO5_IMAGE_URL', defaultValue: '', description: '') }
    environment {
        AWS_REGION_K8S = 'us-west-1'
        K8S_CLUSTER_NAME = 'k8s-batch1'
        K8S_NAMESPACE = 'aryansh-ns'
    }

    stages {
        stage('Setting default namespace') {
            steps {
                    sh '''
                        kubectl config set-context --current --namespace=${K8S_NAMESPACE}
                    '''
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
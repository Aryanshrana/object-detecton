pipeline {
    agent any

    parameters { string(name: 'YOLO5_IMAGE_URL', defaultValue: '', description: '') }
    environment {
        AWS_REGION_K8S = 'us-east-2'
        K8S_CLUSTER_NAME = 'k8s-batch1'
        K8S_NAMESPACE = 'aryansh-ns'
    }
    stages {
        stage('Connecting to the k8s cluster') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                    sh 'aws eks --region ${AWS_REGION_K8S} update-kubeconfig --name ${K8S_CLUSTER_NAME}'
                }
            }
        }
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
                    cd "/var/lib/jenkins/workspace/Yolo5Build/k8s"
                    kubectl apply -f yolo5-deployment.yaml
                '''
            }
        }
    }
}
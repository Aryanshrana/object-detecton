pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Build Yolo5 app and pushing it') {
            steps {
                sh '''
                    aws ecr get-login-password --region us-west-1 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-west-1.amazonaws.com
                    cd yolo5
                    docker build -t aryansh-ecr .
                    docker tag aryansh-ecr:latest 854171615125.dkr.ecr.us-west-1.amazonaws.com/aryansh-ecr:latest
                    docker push 854171615125.dkr.ecr.us-west-1.amazonaws.com/aryansh-ecr:latest
                '''
            }
        }
        stage('Trigger Deploy') {
            steps {
                build job: 'Yolo5Deploy', wait: false, parameters: [
                    string(name: 'YOLO5_IMAGE_URL', value: "854171615125.dkr.ecr.us-west-1.amazonaws.com/aryansh-ecr:latest")
                ]
            }
        }
    }
}
pipeline {
    agent any

    stages {
        stage('install dependency'){
            steps {
                sh '''
                    pip install -r requirements.txt
                   '''
            }
        }
        stage('Unittest') {
            steps {
                sh 'python3 -m pytest --junitxml results.xml tests'
            }
        }
        stage('Lint') {
            steps {
                echo "linting"
            }
        }
        stage('Functional test') {
            steps {
                echo "testing"
            }
        }

    }
}
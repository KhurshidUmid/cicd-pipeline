pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:KhurshidUmid/cicd-pipeline.git'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t my-react-app .'
            }
        }

        stage('Push Docker image') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-password', variable: 'DOCKER_PASS')]) {
                    sh '''
                        echo "$DOCKER_PASS" | docker login -u mydockeruser --password-stdin
                        docker tag my-react-app mydockeruser/my-react-app:latest
                        docker push mydockeruser/my-react-app:latest
                    '''
                }
            }
        }
    }
}

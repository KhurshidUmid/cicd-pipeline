pipeline {
    agent any
    tools {
        nodejs 'node-16'

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-react-app:${env.BRANCH_NAME}")
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying branch ${env.BRANCH_NAME}"
                // Here you could add deployment commands if needed
            }
        }
    }
}


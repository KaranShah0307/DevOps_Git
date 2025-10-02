pipeline {
    agent any

    tools {
        nodejs 'NodeJS 24'
    }

    environment {
        CI = 'true'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'NodeJS-Demo-App', url: 'https://github.com/KaranShah0307/DevOps_Git.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    bat 'echo Deploying the application...'
                    bat 'start /B node server.js'
                    sleep 30
                    bat 'taskkill /F /IM node.exe'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

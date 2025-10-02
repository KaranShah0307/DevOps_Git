pipeline {
    agent any

    tools {
        nodejs 'NodeJS 24' // Use the NodeJS configuration from Jenkins
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
                script {
                    powershell 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    powershell 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    powershell 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy script or commands can be added here
                    powershell 'Write-Host "Deploying the application..."'
                    //powershell 'npm start'
                    //powershell 'node server.js'
                    powershell 'Start-Process -NoNewWindow node server.js'
                    sleep 30
                    powershell 'Stop-Process -Name node -Force'
                }
            }
        }
        
    } // end of Stages

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

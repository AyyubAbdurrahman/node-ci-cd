pipeline {
    agent any

    environment {
        CI = 'true'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AyyubAbdurrahman/node-ci-cd.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Run Integration Tests') {
            steps {
                echo 'Running integration tests...'
                bat 'npm run integration-test'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Tambahkan perintah build jika diperlukan
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to the staging server...'
                // Tambahkan perintah deploy jika diperlukan
            }
        }

        stage('Branch Specific Tests') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Running additional tests for develop branch...'
                powershell 'npm run develop-tests'
            }
        }
    }

    post {
        success {
            emailext(
                subject: 'Build Succeeded', 
                body: 'The build succeeded!',
                to: 'gamingayyub3@gmail.com'  
            )
        }
        failure {
            emailext(
                subject: 'Build Failed', 
                body: 'The build failed.',
                to: 'gamingayyub3@gmail.com'  
            )
        }
    }
}

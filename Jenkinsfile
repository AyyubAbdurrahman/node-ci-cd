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
                sh 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Run Integration Tests') {
            steps {
                echo 'Running integration tests...'
                sh 'npm run integration-test'
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
                powershell 'npm run deploy-staging'
            }
        }

        // Mendukung branching
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
            emailext subject: 'Build Succeeded', 
                     body: 'The build succeeded!',
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
        failure {
            emailext subject: 'Build Failed', 
                     body: 'The build failed.',
                     recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
    }
}

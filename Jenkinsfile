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
                bat 'npm run deploy-staging'
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

    // Mendukung branching
    environment {
        BRANCH_NAME = env.GIT_BRANCH
    }

    stages {
        stage('Branch Specific Tests') {
            when {
                expression {
                    return env.BRANCH_NAME == 'develop'
                }
            }
            steps {
                echo 'Running additional tests for develop branch...'
                bat 'npm run develop-tests'
            }
        }
    }
}

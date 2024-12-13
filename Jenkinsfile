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
                sh '"C:\\Program Files\\Git\\bin\\bash.exe" -c "npm install"'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh '"C:\\Program Files\\Git\\bin\\bash.exe" -c "npm test"'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}

pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your GitHub repository
                git 'https://github.com/alishbahrahman/Tourism-Guide.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies using npm
                script {
                    echo 'Installing dependencies'
                    sh 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run unit tests using npm
                script {
                    echo 'Running tests'
                    sh 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                // Build the application
                script {
                    echo 'Building application'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application
                script {
                    echo 'Deploying application'
                    // Add your deployment steps here
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add cleanup steps if necessary
        }

        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline execution failed!'
        }
    }
}

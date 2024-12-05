pipeline {
    agent any

    environment {
        // Define the repository URL and branch as environment variables
        REPO_URL = 'https://github.com/alishbahrahman/Tourism-Guide.git'
        BRANCH = 'main'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository using Git
                git branch: "${BRANCH}", url: "${REPO_URL}"
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install JavaScript dependencies using npm (or yarn if you're using that)
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image
                sh 'docker build -t simple-web-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Run the Docker container
                sh 'docker run -d -p 8080:8080 --name simple-web-app-container simple-web-app'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                script {
                    // Run your Selenium tests (assuming you are using a JS framework like WebDriverIO or Puppeteer)
                    sh 'npm test'  // Adjust based on your testing framework (e.g., WebDriverIO, Mocha, Jest)
                }
            }
        }
    }

    post {
        always {
            // Clean up the Docker container after the tests
            echo 'Pipeline execution completed!'
            sh 'docker stop simple-web-app-container || true'
            sh 'docker rm simple-web-app-container || true'
        }
    }
}

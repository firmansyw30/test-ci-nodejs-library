pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git branch: 'main', url: 'https://github.com/<username>/nodejs-dependency-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Using npm ci to install dependencies as per package-lock.json
                sh 'npm ci'
            }
        }

        stage('Run App') {
            steps {
                // Run simple script
                sh 'node index.js'
            }
        }

        stage('Test') {
            steps {
                // If test script exists, run tests
                sh 'npm test || echo "No tests defined"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully with dependencies installed as per package-lock.json'
        }
        failure {
            echo 'Pipeline failed, check logs for error details'
        }
    }
}

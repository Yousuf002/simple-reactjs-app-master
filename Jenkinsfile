pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git branch:'main',url: 'https://github.com/Yousuf002/simple-reactjs-app-master'
            }
        }

        stage('Dependency Installation') {
            steps {
                // Install dependencies for the frontend
                sh 'npm install' // Assuming npm is used for dependency management
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image for containerizing the project
                sh 'docker build -t lab10 .'
            }
        }

        stage('Run Docker Image') {
            steps {
                // Run Docker image
                sh 'docker run -d -p 8081:80 lab10'
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push Docker image to Docker Hub
                bat 'docker push lab10'
            }
        }
    }
    
    post {
        always {
            // Clean up after the build
            deleteDir()
        }

        success {
            // Send notification on success
            echo 'Build successful! Sending notification...'
        }

        failure {
            // Send notification on failure
            echo 'Build failed! Sending notification...'
        }
    }
}

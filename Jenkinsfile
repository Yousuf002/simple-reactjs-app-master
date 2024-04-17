pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/Yousuf002/simple-reactjs-app-master'
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
                sh 'docker build -t your-image-name .'
            }
        }

        stage('Run Docker Image') {
            steps {
                // Run Docker image
                sh 'docker run -d -p 8080:80 your-image-name'
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push Docker image to Docker Hub
                sh 'docker push your-docker-hub-username/your-image-name'
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

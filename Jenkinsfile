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
                sh 'docker run -d -p 3000:3000 lab10'
            }
        }

    }

}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {

                    
                    // Build the Docker image
                    sh "docker build -t my-python-app:latest ."
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    // Define image name and tag
                    def imageName = 'my-python-app'
                    def imageTag = 'latest'
                    
                    // Run the Docker container
                    sh "docker run --rm ${imageName}:${imageTag}"
                }
            }
        }
    }

    post {
        always {
            // Clean up any leftover containers or images if needed
            sh 'docker system prune -f'
        }
    }
}

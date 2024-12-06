pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone your Git repository
                git 'https://github.com/asmi29/Practice.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t helloworld-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container
                    sh 'docker run -d -p 5000:5000 --name helloworld-container helloworld-app'
                }
            }
        }

        stage('Clean Up') {
            steps {
                script {
                    // Stop and remove the container (optional cleanup step)
                    sh '''
                    docker stop helloworld-container || true
                    docker rm helloworld-container || true
                    '''
                }
            }
        }
    }
}

pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "docker-webapp"
    }

    stages {
        stage('Checkout Repository') {
            steps {
                git credentialsId: '2efecf4d-abd3-4e84-ad0f-65dc8bbf65f5', url: 'https://github.com/Kanchannishad/docker-webapp.git', branch: 'main'
            }
        }

        stage('Build and Run Docker Compose') {
            steps {
                script {
                    // Stop any existing containers for a clean rebuild
                    bat 'docker-compose down || exit 0'
                    
                    // Build and start both frontend and backend using docker-compose
                    bat 'docker-compose up -d --build'
                }
            }
        }

        stage('Verify Containers') {
            steps {
                script {
                    // Check running containers
                    bat 'docker ps'
                    
                    // Optional: Quick test if ports are up (curl needs to be installed)
                    bat 'curl -I http://localhost:8081 || echo "⚠️ Frontend not reachable"'
                    bat 'curl -I http://localhost:5000 || echo "⚠️ Backend not reachable"'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
        }
        failure {
            echo '❌ Build failed! Please check the Console Output for details.'
        }
    }
}

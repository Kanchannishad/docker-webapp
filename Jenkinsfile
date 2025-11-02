pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    credentialsId: '2efecf4d-abd3-4e84-ad0f-65dc8bbf65f5',
                    url: 'https://github.com/Kanchannishad/docker-webapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t docker-webapp .'
            }
        }

        stage('Run Docker Containers') {
            steps {
                bat 'docker run -d -p 8081:80 docker-webapp'
            }
        }
    }
}

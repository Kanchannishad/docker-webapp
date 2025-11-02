pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Kanchannishad/docker-webapp.git'
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

pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Kanchannishad/docker-webapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker-compose build'
                }
            }
        }

        stage('Run Docker Containers') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}

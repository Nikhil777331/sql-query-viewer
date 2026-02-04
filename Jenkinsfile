pipeline {
    agent any

    stages {
        stage('Pull code') {
            steps {
                git branch: 'main', url: 'https://github.com/Nikhil777331/sql-query-viewer.git'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t sql-viewer .'
            }
        }

        stage('Run Docker container') {
            steps {
                sh '''
                docker stop sql-viewer-app || true
                docker rm sql-viewer-app || true
                docker run -d -p 8501:8501 --name sql-viewer-app sql-viewer
                '''
            }
        }
    }
}


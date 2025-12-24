pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Malticoder/malti-flask-application.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-hello-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker run -d -p 5000:5000 --name flask-container flask-hello-app
                '''
            }
        }
    }
    post {
        success {
            echo "app deployed successfully"
        }
        failure {
            echo "build failed"
            
        }
            
        }
    }

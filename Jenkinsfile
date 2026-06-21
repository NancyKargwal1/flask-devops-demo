pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-demo .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop flask-demo
                docker rm flask-demo
                exit /b 0
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d --name flask-demo -p 5000:5000 flask-demo'
            }
        }
    }
}
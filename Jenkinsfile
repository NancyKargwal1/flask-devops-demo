pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/NancyKargwal1/flask-devops-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t flask-demo .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop flask-demo || true
                docker rm flask-demo || true

                docker run -d \
                --name flask-demo \
                -p 5000:5000 \
                flask-demo
                '''
            }
        }
    }
}
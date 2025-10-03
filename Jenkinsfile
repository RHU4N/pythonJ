pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker-compose -f docker-compose.yml build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image('python:3.9-slim').inside {
                        sh 'pip install -r app/requirements.txt'
                        sh 'python app/test_app.py'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose -f docker-compose.yml up -d'
                }
            }
        }
    }
}
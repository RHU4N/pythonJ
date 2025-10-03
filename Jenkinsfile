pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Iniciando Build..."
                sh 'docker build -t myapp:latest ./app'
            }
        }
        stage('Test') {
            steps {
                echo "Rodando testes..."
                sh 'docker run --rm myapp:latest python test_app.py'
            }
        }
        stage('Deploy') {
            steps {
                echo "Fazendo deploy..."
                sh 'docker-compose -f docker-compose.yml up -d'
            }
        }
    }
    post {
        failure {
            echo "❌ Pipeline falhou!"
        }
    }
}
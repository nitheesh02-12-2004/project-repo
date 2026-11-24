pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t expense-tracker:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker rm -f expense-tracker || true

                    docker run -d \
                    --name expense-tracker \
                    -p 5000:5000 \
                    expense-tracker:latest
                '''
            }
        }
    }
}

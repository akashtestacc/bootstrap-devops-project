pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t bootstrap-site .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '''
                docker stop bootstrap-site >nul 2>&1
                docker rm bootstrap-site >nul 2>&1

                docker run -d -p 8081:80 --name bootstrap-site bootstrap-site
                '''
            }
        }
    }
}
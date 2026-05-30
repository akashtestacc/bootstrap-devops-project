pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t bootstrap-site .'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                docker stop bootstrap-site || exit 0
                docker rm bootstrap-site || exit 0
                docker run -d -p 8081:80 --name bootstrap-site bootstrap-site
                '''
            }
        }
    }
}

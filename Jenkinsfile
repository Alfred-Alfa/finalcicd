pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build --no-cache -t vite-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                /usr/local/bin/docker stop vite-container || echo Container not running
                /usr/local/bin/docker rm vite-container || echo Container not found
                /usr/local/bin/docker run -d -p 8081:80 --name vite-container vite-app
                '''
            }
        }
    }
}


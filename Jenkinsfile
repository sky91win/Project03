pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/sky91win/Project03.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop & remove old container if exists
                sh 'docker stop python-demo-app || true'
                sh 'docker rm python-demo-app || true'

                // Run Flask app on host network so external access works
                sh 'docker run -d --network host --name python-demo-app python-demo-app'
            }
        }
    }
}

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
                sh 'docker stop python-demo-app || true'
                sh 'docker rm python-demo-app || true'

                sh 'docker run -d -p 5000:5000 --name python-demo-app python-demo-app'
            }
        }
    }
}

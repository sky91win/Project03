pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sky91win/Project03.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -upgrade'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name python-demo-app python-demo-app'
            }
        }
    }
}

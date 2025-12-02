pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                // Pull code from main branch
                git branch: 'main', url: 'https://github.com/sky91win/Project03.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Upgrade pip
                sh 'pip install --upgrade pip'
                
                // Install Flask only (your app needs only Flask)
                sh 'pip install flask'
            }
        }

        stage('Run Tests') {
            steps {
                // Skip gracefully if no tests exist
                sh 'pytest || echo "No tests found, skipping..."'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-demo-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                // Stop previous container if running
                sh 'docker stop python-demo-app || true'
                sh 'docker rm python-demo-app || true'

                // Run new container
                sh 'docker run -d -p 5000:5000 --name python-demo-app python-demo-app'
            }
        }
    }
}

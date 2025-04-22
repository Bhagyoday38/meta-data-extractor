pipeline {
    agent any

    environment {
        APP_DIR = 'exif-flask-app'
        VENV = 'venv'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Shlok-Aashay/exif-flask-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // You can integrate pytest or unittest here
                sh './venv/bin/python -m unittest discover -s tests'
            }
        }

        stage('Deploy') {
            steps {
                // Simple example: run the app locally
                sh 'nohup ./venv/bin/python app.py &'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}

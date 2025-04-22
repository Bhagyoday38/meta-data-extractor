pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Bhagyoday38/exif-flask.git'
            }
        }

        stage('Set Up Environment') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install --upgrade pip'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh '. venv/bin/activate && pytest tests/'
            }
        }

        stage('Run Flask App') {
            steps {
                sh '. venv/bin/activate && nohup python app.py &'
            }
        }
    }

    post {
        success {
            echo 'Build and Deploy Successful!'
        }
        failure {
            echo 'Build failed. Check the logs.'
        }
    }
}
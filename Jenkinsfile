pipeline {
    agent any

    environment {
        PATH = "C:\\Windows\\System32;${env.PATH}"
        PYTHONPATH = "."
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Environment Check') {
            steps {
                bat '''
                echo Checking Python installation...
                where python
                python --version
                '''
            }
        }

        stage('Setup') {
            steps {
                bat '''
                echo Installing dependencies...
                python -m pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                echo Running tests with pytest...
                pytest tests/
                '''
            }
        }

        stage('Done') {
            steps {
                echo '✅ Tests passed.'
            }
        }
    }

    post {
        always {
            echo '📦 Pipeline completed.'
        }
        failure {
            echo '❌ Build or tests failed.'
        }
    }
}

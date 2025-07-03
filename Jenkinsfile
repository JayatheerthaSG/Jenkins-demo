pipeline {
    agent any

    environment {
        PYTHONPATH = '.'
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
                echo Checking if Python is installed and available in PATH...
                where python || (echo ❌ Python not found in PATH && exit /b 1)
                python --version
                '''
            }
        }

        stage('Build') {
            steps {
                echo '⚙️ No build needed for Python script, just a demo'
            }
        }

        stage('Test') {
            steps {
                bat '''
                echo Running unit tests...
                python -m unittest test_app.py || (echo ❌ Unit tests failed && exit /b 1)
                '''
            }
        }
    }

    post {
        always {
            echo '📦 Pipeline finished'
        }
        failure {
            echo '❌ Build or test stage failed.'
        }
    }
}

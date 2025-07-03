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
                bat 'where python'
                bat 'python --version'
            }
        }

        stage('Build') {
            steps {
                echo 'No build needed for Python script, just a demo'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests'
                bat 'python -m unittest test_app.py'
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline finished'
        }
        failure {
            echo '❌ Build or test failed'
        }
    }
}

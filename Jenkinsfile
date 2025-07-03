pipeline {
    agent any

    stages {
        stage('Environment Check') {
            steps {
                bat 'C:\\Windows\\System32\\cmd.exe /c "where python"'
                bat 'C:\\Windows\\System32\\cmd.exe /c "python --version"'
            }
        }

        stage('Test') {
            steps {
                bat 'C:\\Windows\\System32\\cmd.exe /c "python -m unittest test_app.py"'
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

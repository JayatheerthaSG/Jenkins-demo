pipeline {
    agent any

    environment {
        PATH = "C:\\Windows\\System32;${env.PATH}"
        PYTHONPATH = "."
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

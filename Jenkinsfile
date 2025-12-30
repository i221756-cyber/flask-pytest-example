pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Repository already cloned by Jenkins SCM'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                python -m venv venv
                venv\\Scripts\\activate && pip install -r requirements.txt
                '''
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building Flask application'
                bat 'echo Build completed successfully'
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application (simulated)'
                bat '''
                if not exist C:\\deploy mkdir C:\\deploy
                xcopy /E /I /Y . C:\\deploy
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}

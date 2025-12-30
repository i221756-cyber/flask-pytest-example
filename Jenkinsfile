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
                bat 'python -m venv venv'
                bat 'venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat 'venv\\Scripts\\activate && pytest'
            }
        }

        stage('Build Application') {
            steps {
                bat 'mkdir build'
                bat 'xcopy /E /I /Y . build'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'mkdir C:\\temp\\flask-deploy'
                bat 'xcopy /E /I /Y build C:\\temp\\flask-deploy'
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


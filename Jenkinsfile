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
                sh 'python -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh '. venv/bin/activate && pytest'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building Flask application'
                sh 'mkdir -p build'
                sh 'cp -r . build/'
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Simulating deployment'
                sh 'mkdir -p /tmp/flask-deploy'
                sh 'cp -r build/* /tmp/flask-deploy/'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}

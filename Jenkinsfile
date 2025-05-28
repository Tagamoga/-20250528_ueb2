pipeline {
    agent any
    environment {
        VENV_PATH = "venv"
    }
    stages {
        stage('Build') {
            steps {
                sh 'python -m venv $VENV_PATH'
                sh './$VENV_PATH/bin/pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh './$VENV_PATH/bin/pytest tests/ --junitxml=test-results.xml'
            }
        }
    }
    post {
        always {
            junit 'test-results.xml'
        }
    }
}
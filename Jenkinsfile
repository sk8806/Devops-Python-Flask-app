pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                . venv/bin/activate
                export PYTHONPATH=$PWD
                pytest
                '''
            }
     }
        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t flask-app:1.0 .
                '''
           }
	}
    }

}

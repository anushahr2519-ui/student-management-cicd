
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m pytest -v'
            }
        }

        stage('Run Application') {
            steps {
                bat 'python app.py'
            }
        }

        stage('Package Release') {
            steps {
                bat '''
                    if not exist release mkdir release
                    copy /Y app.py release\\app.py
                    copy /Y requirements.txt release\\requirements.txt
                '''
                archiveArtifacts artifacts: 'release/**',
                                 fingerprint: true
            }
        }
    }
}

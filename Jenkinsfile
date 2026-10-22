
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
                bat '"C:\Users\Admin\AppData\Local\Programs\Python\Python312\python.exe" -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat '"C:\Users\Admin\AppData\Local\Programs\Python\Python312\python.exe" -m pytest -v'
            }
        }

        stage('Run Application') {
            steps {
                bat '"C:\Users\Admin\AppData\Local\Programs\Python\Python312\python.exe" app.py'
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

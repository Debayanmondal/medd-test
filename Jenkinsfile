pipeline {
    agent any

    environment {
        FRONTEND_DIR = '/medcare'
        BACKEND_DIR = '/medcare-server'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Debayanmondal/medd-test.git'
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                dir("${env.FRONTEND_DIR}") {
                    sh 'npm install'
                }
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                dir("${env.BACKEND_DIR}") {
                    sh 'npm install && sudo npm i pm2 -g'
                }
            }
        }

        stage('Start Backend') {
            steps {
                dir("${env.BACKEND_DIR}") {
                    sh 'pm2 start app.js'
                }
            }
        }
    }

    post {
        always {
           // cleanWs()
            echo "Pipeline End"
        }
    }
}

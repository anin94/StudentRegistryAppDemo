pipeline {
    agent any

    environment {
        NODE_VERSION = '18.x'
    }

    tools {
        nodejs "${NODE_VERSION}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'npm install'
                    } else {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Start application and Run Tests') {
            steps {
                script {
                    sh 'npm start &'
                    sh 'wait-on localhost:8090' // Wait for the application to start
                    sh 'npm test'
                }
            }
        }
    }

    post {
        always {
           echo 'CI pipeline completed.'
        }
    }
}
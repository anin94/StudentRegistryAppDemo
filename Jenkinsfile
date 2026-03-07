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
                git branch: 'main', url: 'https://github.com/anin94/StudentRegistryAppDemo'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                
             bat 'npm install'
                
            }
        }

        stage('Start application and Run Tests') {
            steps {
                script {
                    bat 'npm start &'
                    bat 'wait-on localhost:8090' // Wait for the application to start
                    bat 'npm test'
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
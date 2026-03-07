pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/anin94/StudentRegistryAppDemo'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
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
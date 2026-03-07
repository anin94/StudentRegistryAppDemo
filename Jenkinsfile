pipeline {
    agent any

tools {
    nodejs 'NodeJS'
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
                    sh 'npm install'
                }
            }
        }

        stage('Start application and Run Tests') {
            steps {
                script {
                    sh 'start /b npm start'  
                }
            }
        }

         stage('Run Tests') {
            steps {
                script {
                    sh 'start npm test'  
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
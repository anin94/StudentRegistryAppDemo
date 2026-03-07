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
                sh 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                // Стартираме приложението във фонов режим и изчакваме да се стартира
                sh 'nohup npm start &'
                sh 'sleep 5' // изчакваме 5 секунди да се стартира сървъра
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            echo 'CI pipeline completed.'
        }
    }
}
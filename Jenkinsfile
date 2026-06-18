pipeline {
    agent {
        docker {
            image 'node:18'
            args '-p 3000:3000'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npx jest'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! All tests passed.'
        }
        failure {
            echo 'Pipeline failed. Check the logs above for which stage failed.'
        }
    }
}
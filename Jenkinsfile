pipeline {
    agent any

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code is available'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci --ignore-scripts'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm pack --dry-run'
            }
        }
    }

    post {
        success {
            echo 'CI pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Review the logs.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}

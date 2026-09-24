pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }
        stage('Parallel Checks') {
            parallel {
                stage('Unit Check') {
                    steps {
                        bat 'python unit_check.py'
                    }
                }
                stage('Integration Check') {
                    steps {
                        bat 'python integration_check.py'
                    }
                }
            }
        }
        stage('Summary') {
            steps {
                echo 'Parallel checks finished!'
            }
        }
    }
    post {
        success {
            echo 'All checks passed!'
        }
        failure {
            echo 'At least one check failed!'
        }
    }
}

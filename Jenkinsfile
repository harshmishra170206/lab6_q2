pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/harshmishra170206/lab6_q2.git']])
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

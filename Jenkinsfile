pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                sh 'git branch'
            }
        }

        stage('Build & Unit Test') {
            steps {
                echo 'Running Application Build...'
                // Simulating build time
                sleep time: 5, unit: 'SECONDS'
                echo 'Running JUnit Tests...'
            }
        }

        stage('Parallel Quality Checks') {
            parallel {
                stage('SonarQube Analysis') {
                    steps {
                        echo 'Scanning code quality with SonarQube...'
                        sleep time: 7, unit: 'SECONDS'
                    }
                }
                stage('Security Scan') {
                    steps {
                        echo 'Running OWASP Dependency Check...'
                        sleep time: 5, unit: 'SECONDS'
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying branch ${env.BRANCH_NAME} to environment..."
                sleep time: 4, unit: 'SECONDS'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs in Blue Ocean.'
        }
    }
}

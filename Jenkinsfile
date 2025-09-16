pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Static Code Analysis (ESLint)') {
            steps {
                sh 'npx eslint . || true'
            }
        }

        stage('Vulnerability Scan (npm audit)') {
            steps {
                sh 'npm audit --json || true'
            }
        }

        stage('Vulnerability Scan (Snyk)') {
            steps {
                sh 'npx snyk test || true'
            }
        }
    }
}


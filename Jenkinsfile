pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/s223930381/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Security Scan (npm audit)') {
            steps {
                sh 'npm audit || true'
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Jenkins Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """Build finished with status: ${currentBuild.currentResult}
                Check console output at: ${env.BUILD_URL}""",
                to: 's223930381@deakin.edu.au'
            )
        }
    }
}


pipeline {
    agent any

    stages {


        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/s223930381/8.2CDevSecOps.git'
            }
        }

(Update Jenkinsfile with email notifications)
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

<<<<<<< HEAD
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
=======
        stage('Run Tests') {
            steps {
                sh 'npm test || true' // keep pipeline running even if tests fail
            }
            post {
                always {
                    emailext (
                        to: 's223930381@deakin.edu.au',
                        subject: "Jenkins Build - Test Stage: ${currentBuild.currentResult}",
                        body: """Hello,  

The **Test stage** has completed with status: ${currentBuild.currentResult}.  

Check Jenkins console logs for more details.  

Thanks,  
Your Jenkins Pipeline  
"""
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                sh 'npm audit || true' // run audit and ignore exit codes
            }
            post {
                always {
                    emailext (
                        to: 's223930381@deakin.edu.au',
                        subject: "Jenkins Build - Security Scan: ${currentBuild.currentResult}",
                        body: """Hello,  

The **Security Scan stage** has completed with status: ${currentBuild.currentResult}.  

See attached logs for vulnerabilities found.  

Thanks,  
Your Jenkins Pipeline  
""",
                        attachLog: true
                    )
                }
>>>>>>> 2a50075 (Update Jenkinsfile with email notifications)
            }
        }
    }
}


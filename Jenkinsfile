pipeline {
    agent any

    environment {
        SNYK_TOKEN = credentials('snyk-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Static code analysis (Bandit)') {
            steps {
                sh 'pip install bandit'
                sh 'bandit -r app'
            }
        }

        stage('Security scan (Snyk)') {
            steps {
                sh 'snyk test'
            }
        }

        stage('Docker image scan (Trivy)') {
            steps {
                sh 'docker build -t myapp .'
                sh 'trivy image --exit-code 1 myapp'
            }
        }

        stage('OWASP ZAP Scan') {
            steps {
                sh 'docker run -d -p 5000:5000 myapp'
                sh 'docker run --rm -v $(pwd):/zap/wrk:rw -t owasp/zap2docker-stable zap-baseline.py -t http://localhost:5000'
            }
        }
    }

    post {
        always {
            junit '**/test-reports/*.xml'
        }
        failure {
            mail to: 'admin@percevalfox.com',
                 subject: "Pipeline failed",
                 body: "The pipeline failed."
        }
    }
}

pipeline {
    agent any

    environment {
        GIT_URL = 'https://github.com/Sivasankar22/Devops_priacc.git'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
                git branch: 'main', url: "${GIT_URL}"
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build Artifact') {
            steps {
                sh 'zip -r build.zip app.js package.json test.js'
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build.zip', fingerprint: true
            }
        }
        stage('Notify') {
            steps {
                echo "✅ Build and tests successful! (Slack/Email notification placeholder)"
            }
        }
    }

    post {
        failure {
            echo "❌ Build failed. Please check logs."
        }
    }
}

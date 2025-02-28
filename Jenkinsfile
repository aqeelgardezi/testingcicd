pipeline {
    agent any
    tools {
        nodejs 'Node18'  // Assuming you updated to 18 as per commit message
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aqeelgardezi/testingcicd.git'
            }
        }
        stage('Setup Frontend') {
            steps {
                dir('frontend') {
                    // Cache npm dependencies
                    sh 'npm ci --prefer-offline --cache /var/lib/jenkins/.npm'
                    sh 'npm run build'
                }
            }
        }
        stage('Finish') {
            steps {
                echo 'Setup complete!'
            }
        }
    }
    // Post-build cleanup (optional)
    post {
        always {
            cleanWs()  // Clean workspace to save disk space
        }
    }
}

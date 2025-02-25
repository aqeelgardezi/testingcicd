pipeline {
    agent any
    tools {
        nodejs 'Node16'
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
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Setup Backend') {
            steps {
                dir('backend') {
                    sh 'composer install --no-interaction'
                }
            }
        }
        stage('Finish') {
            steps {
                echo 'Setup complete!'
            }
        }
    }
}
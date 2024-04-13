pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy application to Render
                sh 'render deploy'
            }
        }
    }
}

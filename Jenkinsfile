pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Add commands to install required software
                sh 'npm install'
            }
        }
        stage('Deploy') {
            steps {
                // Add commands to deploy to Render
                sh 'node server'
            }
        }
    }
}

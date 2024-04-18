pipeline {
    agent any
    
    tools {
        // Specify the Node.js tool installation
        nodejs 'nodejs'
    }
    
    stages {
        stage('clone-project') {
            steps {
                // Clone code from GitHub repository
                git branch: 'master', url: 'https://github.com/OndiekiFrank/gallery'
            }
        }
        
        stage('build-project') {
            steps {
                // Set up Node.js environment and install dependencies
                sh 'npm install'
            }
        }
        
        stage('test-project') {
            steps {
                // Run tests
                sh 'npm test'
            }
            post {
                failure {
                    // Send Slack notification on test failure
                    slackSend(channel: '#yourfirstnameip1', color: 'danger', message: "test failed")
                }
            }
        }
    }
}

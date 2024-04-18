pipeline {
    agent any
    
    stages {
        stage('Clone Project') {
            steps {
                // Clone code from GitHub repository
                git branch: 'master', url: 'https://github.com/OndiekiFrank/gallery'
            }
        }
        
        stage('Build') {
            steps {
                // Set up Node.js environment and install dependencies
                script {
                    def nodeHome = tool name: 'NodeJS', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodeHome}/bin:${env.PATH}"
                    sh 'npm install'
                }
            }
        }
        
        stage('Test Project') {
            steps {
                // Run tests
                sh 'npm test'
            }
            post {
                failure {
                    // Send Slack notification on test failure
                    slackSend(channel: '#yourfirstnameip1', color: 'danger', message: "Test failed")
                }
            }
        }
    }
}

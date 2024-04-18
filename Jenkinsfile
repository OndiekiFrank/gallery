pipeline {
    tools{
        nodejs 'nodejs'
    }
    agent any
    
    stages {
        stage('Git Clone') {
            steps {
                // Clone code from GitHub repository
                git branch: 'master', url: 'https://github.com/OndiekiFrank/gallery'
            }
        }
        
        stage('Build') {
            steps {
                // Set up Node.js environment and install dependencies
                    sh 'npm install'
                }
            }
        }
        
        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
            post {
                failure {
                    slackSend(channel: '#yourfirstnameip1', color: 'danger',
                                  message: "test failed")
                }
            }
        }
    }


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
        
        stage('Deploy to Render') {
            steps {
                // Log in to Render
                withCredentials([usernamePassword(credentialsId: 'render_credentials', passwordVariable: 'RENDER_PASSWORD', usernameVariable: 'RENDER_EMAIL')]) {
                    sh "render login --email ondiekifrank021@gmail.com --password Utmost37*Frank"
                }
                
                // Deploy to Render
                sh 'render deploy --branch main --localPath . --name gallery'
            }
            post {
                success {
                    // Send Slack notification on successful deployment
                    slackSend(channel: '#yourfirstnameip1', color: 'good', message: "Deployment successful. View the site at https://gallery-noc3.onrender.com")
                }
                failure {
                    // Send Slack notification on deployment failure
                    slackSend(channel: '#yourfirstnameip1', color: 'danger', message: "Deployment failed")
                }
            }
        }
    }
}

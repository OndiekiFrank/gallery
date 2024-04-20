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
        }
        
        stage('Deploy-to-Render') {
            steps {
                // Deployment step
                script {
                    // Install render-cli
                    sh 'curl -O https://github.com/render-oss/render-cli/releases/download/v0.1.11/render-linux-x86_64'

                    // Create bin directory in the project's root directory
                    sh 'mkdir -p bin'

                    // Move render-cli to bin directory 
                    sh 'mv render-linux-x86_64 bin/'

                    // Ensure executable has permissions 
                    sh 'chmod +x bin/render'

                    // Deploy your application
                    sh 'render blueprint launch'
                }
            }
            // Assuming successful deployment
            post {
                success {
                    script {
                        def buildId = env.BUILD_ID
                        def renderLink = 'https://gallery2-u5iz.onrender.com/'

                        slackSend(channel: '#yourfirstnameip1', color: 'good',
                                  message: "Deployment successful! Build ID: ${buildId}\nRender Link: ${renderLink}")
                    }
                }
            }
        }
    }
}

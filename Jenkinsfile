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
                    // Replace the original URL with the updated one
                    sh 'curl -O https://github.com/render-oss/render-cli/releases/download/v0.1.11/render-linux-x86_64'

                    sh 'ls -l'

                    // Create bin directory in the project's root directory
                    sh 'mkdir -p bin'

                    // Move render-cli to bin directory 
                    sh 'mv render-linux-x86_64 bin/'

                    sh 'ls -l bin'

                    // Ensure executable has permissions 
                    sh 'chmod +x bin/render-linux-x86_64'

                    sh 'ls -l bin'

                    // Deploy your application with the updated URL
                    sh 'curl -X POST https://api.render.com/deploy/srv-coge47o21fec73d8drj0?key=xfTK7pCbBmc'
                }
            }
            // Assuming successful deployment
            post {
                success {
                    script {
                        def buildId = env.BUILD_ID
                        def renderLink = 'https://gallery-noc3.onrender.com'

                        slackSend(channel: '#yourfirstnameip1', color: 'good',
                                  message: "Deployment successful! Build ID: ${buildId}\nRender Link: ${renderLink}")
                    }
                }
            }
        }
    }
}

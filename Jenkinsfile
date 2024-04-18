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
                    // If tests fail, no action needed
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
        }
    }
}

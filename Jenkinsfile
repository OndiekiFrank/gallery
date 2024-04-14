pipeline {
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
                script {
                    def nodeHome = tool name: 'NodeJS', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodeHome}/bin:${env.PATH}"
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
                    // Send email notification on test failure
                    emailext body: 'The tests failed. Please check the Jenkins console output for more details.',
                             subject: 'Test Failure Notification',
                             to: 'ondiekifrank021@gmail.com'
                }
            }
        }
    }
}

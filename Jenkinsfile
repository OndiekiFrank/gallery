pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                // Clone code from GitHub repository
                git branch: 'master', url: 'https://github.com/OndiekiFrank/gallery'
            }
        }
        stage('Build') {
            steps {
                // Install Node.js dependencies
                script {
                    // Set up Node.js environment
                    def nodeHome = tool name: 'NodeJS', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodeHome}/bin:${env.PATH}"

                    // Install npm dependencies
                    sh 'npm install'
                }
            }
        }
    }
}

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
        stage('Deploy to Heroku') {
            steps {
                // Login to Heroku CLI
                script {
                    def herokuAuthToken = sh(script: 'heroku auth:token', returnStdout: true).trim()
                    withCredentials([string(credentialsId: 'heroku-auth-token', variable: 'HEROKU_AUTH_TOKEN')]) {
                        sh "echo $HEROKU_AUTH_TOKEN | base64 --decode > \$HOME/.netrc"
                    }
                }
                
                // Deploy to Heroku
                sh 'git push heroku master'
            }
        }
    }
}

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
        
        stage('Deploy') {
            steps {
                // Authenticate with Heroku CLI
                withCredentials([string(credentialsId: 'HRKU-8ef548af-28a8-48c2-a35b-80d4061794d8', variable: 'HEROKU_API_KEY')]) {
                    sh 'git config --global user.email "frankline.ondieki@student.moringaschool.com"'
                    sh 'heroku container:login'
                }
                
                // Push to Heroku
                sh 'git push https://heroku:$HEROKU_API_KEY@git.heroku.com/pacific-sea-19354.git master'
            }
        }
    }
}

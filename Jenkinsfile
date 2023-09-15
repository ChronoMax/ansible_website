pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }

        stage('Deploy to Ubuntu Server') {
            steps {
                script {
                    // Define your Ubuntu server details
                    def serverHost = '172.16.1.3'
                    def serverUser = 'student'
                    def remotePath = '/var/www/html/'

                    // Copy the HTML and CSS files to the server
                    sshagent(['ssh-creds']) {
                        sh "scp -r ./* ${serverUser}@${serverHost}:${remotePath}"
                    }
                }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }

        stage('Delete Existing Files') {
            steps {
                script {
                    def serverHost = '172.16.1.4'
                    def serverUser = 'student'

                    // Delete existing HTML and CSS files
                    sshagent(['ssh-creds']) {
                        sh "ssh ${serverUser}@${serverHost} 'rm -rf /var/www/html/*'"
                    }
                }
            }
        }

        stage('Deploy to Ubuntu Server') {
            steps {
                script {
                    // Define your Ubuntu server details
                    def serverHost = '172.16.1.4'
                    def serverUser = 'student'
                    def remotePath = '/var/www/html/'

                    // Copy the HTML and CSS files to the server
                    sshagent(['ssh_creds']) {
                        sh "scp -r ./* ${serverUser}@${serverHost}:${remotePath}"
                    }
                }
            }
        }
    }
}

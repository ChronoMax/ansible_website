pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Perform any build steps if necessary (e.g., minifying CSS or JS)
                echo "Building website..."
                // Add your build commands here
            }
        }

        stage('Test') {
            steps {
                // Perform any tests on your website (e.g., link checking)
                echo "Testing website..."
                // Add your test commands here
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the website to the Ubuntu server
                echo "Deploying website..."
                sshagent(['your-ssh-credentials-id']) {
                    // Use SSH to copy the website files to the server
                    sh "scp -r ./* student@172.16.1.4:/var/www/html/"
                }
            }
        }
    }

    post {
        success {
            echo "Website deployed successfully!"
        }
        failure {
            echo "Website deployment failed."
        }
    }
}

pipeline {
    agent any

    environment {
        REMOTE_HOST = '192.168.1.50'
        SSH_CREDENTIALS = 'osboxes'
    }

    stages {
        stage('Install Apache2') {
            steps {
                sshagent([SSH_CREDENTIALS]) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no osboxes@${REMOTE_HOST} "sudo apt update && sudo apt install -y apache2"
                    '''
                }
            }
        }

        stage('Restart Apache2') {
            steps {
                sshagent([SSH_CREDENTIALS]) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no osboxes@${REMOTE_HOST} "sudo systemctl restart apache2"
                    '''
                }
            }
        }
    }
}

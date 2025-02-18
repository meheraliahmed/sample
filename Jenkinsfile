pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(
                    configName: 'LocalServer',
                    transfers: [sshTransfer(
                        sourceFiles: '**/*.html',
                        removePrefix: '',
                        remoteDirectory: '/var/www/html',
                        execCommand: 'sudo systemctl restart apache2'
                    )],
                    usePromotionTimestamp: false,
                    useWorkspaceInPromotion: false,
                    verbose: true
                )])
            }
        }
    }
}

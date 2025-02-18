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
                cifsPublisher(publishers: [cifsPublisherDesc(
                    configName: 'LocalServer',
                    transfers: [cifsTransfer(
                        sourceFiles: '**/*.html',
                        removePrefix: '',
                        remoteDirectory: 'html',
                        execCommand: 'nginx -s reload'
                    )],
                    usePromotionTimestamp: false,
                    useWorkspaceInPromotion: false,
                    verbose: true
                )])
            }
        }
    }
}

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
                script {
                    def remote = [:]
                    remote.name = 'LocalServer'
                    remote.host = 'localhost'
                    remote.user = 'your-username'
                    remote.password = 'your-password'
                    remote.allowAnyHosts = true

                    sshPublisher(publishers: [sshPublisherDesc(
                        configName: 'LocalServer',
                        transfers: [sshTransfer(
                            sourceFiles: '**/*.html',
                            removePrefix: '',
                            remoteDirectory: 'C:/nginx/html',
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
}

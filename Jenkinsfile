pipeline {
    agent {
        label 'agent-node01'  // Jenkins agent label
    }
    stages {
        stage('Build') {
            steps {
                script {
                    docker.image('node:18-alpine').inside('--user root') {
                        sh '''
                            echo 'Building inside Docker container...'
                            ls -la
                            node --version
                            npm --version
                            npm run build
                            npm ci
                            
                            # Run the build
                            npm run build
                            
                            ls -la
                            echo 'Finished building inside Docker container...'
                        '''
                    }
                }
            }
        }
    }
}

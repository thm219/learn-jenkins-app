pipeline {
    agent {
        label 'agent-node01'  // This is where the node agent is specified
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Run the build inside a Docker container
                    docker.image('node:18-alpine').inside {
                        sh '''
                            echo 'Building inside Docker container...'
                            ls -la
                            node --version
                            npm --version
                            npm install
                            npm list react-scripts
                            npm run build
                            npm ci
                            ls -la
                            echo 'Finish to build inside Docker container...'
                        '''
                    }
                }
            }
        }
    }
}
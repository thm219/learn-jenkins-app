pipeline {
    agent {
        label 'agent-node01'  // This is where the node agent is specified
    }
    stages {
        stage('Front-end') {
            steps {
                script {
                    // Run the build inside a Docker container
                    docker.image('node:22.14.0-alpine3.21').inside {
                        sh '''
                            echo 'Building inside Docker container...'
                            node --version
                            pwd
                            ls -la
                            touch test.txt
                        '''
                    }
                }
            }
        }
    }
}
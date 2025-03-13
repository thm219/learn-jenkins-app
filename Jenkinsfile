pipeline {
    agent {
        label 'agent-node01'  // Jenkins agent label
    }

    /*
    stages {
        stage('Build') {
            steps {
                script {
                    docker.image('node:18-alpine').inside('--user root') {
                        sh '''
                            echo 'Building inside Docker container...'
                            ls -la
                            whoami
                            node --version
                            npm --version
                            npm ci
                            npm run build        
                            ls -la
                            echo 'Finished building inside Docker container...'
                        '''
                    }
                }
            }
        }
    */

        stage ('Test') {
            steps {
                script {
                    docker.image('node:18-alpine').inside('--user root') {
                        sh '''
                            echo 'Test inside Docker container...'
                            ls -la
                            test -f build/index.html
                            npm test
                            ls -la
                            echo 'Finished test stage inside Docker container...'
                        '''
                    } 
                }
            }
        }
    }

}

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
                            
                            # Ensure clean dependencies
                            rm -rf node_modules package-lock.json
                            npm cache clean --force
                            
                            # Install dependencies
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

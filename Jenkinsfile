pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-e HOME=/tmp'
                    reuseNode true
                }
            } 
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm config set cache $WORKSPACE/.npm
                    npm ci 
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
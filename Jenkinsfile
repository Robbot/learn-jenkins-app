pipeline {
    agent any

    stages {
        stage('Debug') {
        steps {
        sh '''
        whoami
        id
        pwd
        echo HOME=$HOME
        env | sort
        ls -ld /
        '''
        }
    }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
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
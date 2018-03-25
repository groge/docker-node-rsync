pipeline {
    agent {
        docker {
            image 'groge/node-rsync'
            args '-p 30000:3000'
        }
    }
    stages {
        stage('NPM Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deliver') {
            steps {
                sh 'rsync -av --delete --exclude ".git" ./dist/* /app/client/'
            }
        }
    }
}

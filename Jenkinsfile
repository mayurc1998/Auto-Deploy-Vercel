pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {
        stage('Install') {
            steps {
                sh '''
                export PATH=$PATH:/home/mayur/.nvm/versions/node/v22.13.1/bin
                node -v
                npm -v
                npm install
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Skipping tests - no test script found'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
            }
        }
    }
}
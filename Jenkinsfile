pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
        PATH = "/home/mayur/.nvm/versions/node/v22.13.1/bin:${env.PATH}"

    }

    stages {
        stage('Install') {
            steps {
                sh '''
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
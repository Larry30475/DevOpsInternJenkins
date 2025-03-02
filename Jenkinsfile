pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    stages {
        stage('checkout') {
            steps {
                sh 'git clone ' + env.GIT_URL
            }
        }
        stage('install') { 
            steps {
                sh 'npm install'
            }
        }
        stage('test') {
            steps {
                sh 'npm test'
            }
        }
        stage('build') {
            steps {
                sh 'npm run start'
            }
        }
    }
}
pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    stages {
        stage('checkout') {
            steps {
                git url: env.GIT_URL
            }
        }
        stage('install') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Code Quality & Tests') {
            parallel {
                stage('Lint') {
                    steps {
                        sh 'npm run lint'
                    }
                }
                stage('Test') {
                    steps {
                        retry(2) {
                            sh 'npm test'
                        }
                    }
                }
            }
        }
    }
}
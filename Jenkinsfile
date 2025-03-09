pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment {
        SLACK_WEBHOOK_URL = credentials('slack-webhook')
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
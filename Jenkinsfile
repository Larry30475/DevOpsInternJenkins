pipeline {
    agent any // run on any available agent
    tools {
        nodejs 'NodeJS' // use NodeJS tool
    }
    stages {
        stage('checkout') {
            steps {
                git url: env.GIT_URL // checkout the code
            }
        }
        stage('install') { 
            steps {
                sh 'npm install' // install dependencies
            }
        }
        stage('Code Quality & Tests') {
            parallel {
                stage('Lint') {
                    steps {
                        sh 'npm run lint' // lint the code
                    }
                }
                stage('Test') {
                    steps {
                        retry(2) {
                            sh 'npm test' // retry 2 times if failed
                        }
                    }
                }
            }
        }
    }
}

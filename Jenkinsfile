pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git env.GIT_URL // checkout the code
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
            retry(count: 2) {
              sh 'npm test'
            }

          }
        }

      }
    }

  }
  tools {
    nodejs 'NodeJS'
  }
}
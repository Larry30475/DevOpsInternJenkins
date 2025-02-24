pipeline {
  agent any
  stages {
    stage('install') {
      parallel {
        stage('install') {
          steps {
            sh 'npm install'
          }
        }

        stage('Check ') {
          steps {
            sh '''node -v
npm -v'''
          }
        }

      }
    }

    stage('test') {
      steps {
        sh 'npm test'
      }
    }

    stage('build') {
      steps {
        sh 'npm run build'
      }
    }

  }
}
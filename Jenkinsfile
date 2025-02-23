pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        sh 'git clone https://github.com/Peter-Odo/nodejs_test.git'
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
        sh 'npm run build'
      }
    }

  }
}
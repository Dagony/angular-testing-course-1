pipeline {
  agent {
    docker 'node:14-alpine'
  }
  stages {
    stage('Restore') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run-script build-and-start:prod'
      }
    }
    stage('Unit Test') {
      steps {
        sh 'npm run-script test'
      }
    }
    stage('E2E Test') {
      steps {
        sh 'npm run-script e2e'
      }
    }
  }
}

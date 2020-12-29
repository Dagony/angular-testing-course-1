pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
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

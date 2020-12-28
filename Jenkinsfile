pipeline {
  agent {
    any { image 'node:14-alpine' }
  }

  environment {
    CI = true
  }

  stages {
    stage('Install dependencies') {
      steps {
        sh 'npm install --silent'
        sh 'node --version'
      }
    }


    stage('Build Angular') {
      steps {
        sh 'node_modules/@angular/cli/bin/ng build'
      }
    }

    stage('Test Angular') {
      steps {
        sh 'node_modules/@angular/cli/bin/ng test'
      }
    }

    stage('Test Angular E2E') {
      steps {
        sh 'npm run e2e'
      }
    }
  }
}

pipeline {
  agent {
    docker {
      image 'node'
    }
  }

  stages {
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Run unit tests') {
      steps {
        sh 'npm test'
      }
    }

    stage('Run e2e tests') {
      steps {
        sh 'npm run e2e'
      }
    }
  }
}

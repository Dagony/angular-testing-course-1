pipeline {
  agent {
    docker {
      image 'cypress/base:10'
    }
  }

  stages {
    stage('build') {
      steps {
        checkout scm
        echo "Running build ${env.BUILD_ID} on ${env.JENKINS_URL}"
        sh 'npm ci'
        sh 'npm run cy:verify'
      }
    }
    stage('start local server') {
      steps {
        sh 'nohup npm run build-and-start:prod &'
      }
    }
    stage('cypress parallel tests') {
      steps {
        echo 'Running build ${env.BUILD_ID}'
        sh 'npm run e2e'
      }
    }
  }

  post {
    always {
      echo 'Stopping local server'
      sh 'pkill -f http-server'
    }
  }
}

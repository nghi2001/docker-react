pipeline {
  agent any
  stages {
    stage('checkout_code') {
      steps {
        git(url: 'https://github.com/nghi2001/docker-react', branch: 'dev')
      }
    }

    stage('shell') {
      steps {
        sh 'ls -la'
      }
    }

  }
}
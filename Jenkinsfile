pipeline {
  agent any
  stages {
    stage('checkout_code') {
      steps {
        git(url: 'https://github.com/nghi2001/docker-react', branch: 'dev')
      }
    }

    stage('build') {
      steps {
        sh 'docker build -t react -f Dockerfile.dev .'
      }
    }
    stage('test') {
      steps {
        sh 'docker run -e react npm run test'
      }
    }
    stage('push') {
      steps {
        sh 'docker login -u nguyenduynghi2001 -p Nghi@#2001'
        sh 'docker tag react nguyenduynghi2001/dk-react'
        sh 'docker push nguyenduynghi2001/dk-react'
        sh 'docker image rm nguyenduynghi2001/dk-react'
      }
    }
    stage('deploy') {
      steps {
        sh 'echo "Nghi"'
      }
    }

  }
}
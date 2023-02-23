pipeline {
  agent any
  stages {
    stage('checkout_code') {
      steps {
        git(url: 'https://github.com/nghi2001/docker-react', branch: 'dev')
      }
    }
  stage('ssh') {
    steps {
      sshagent(credentials: ['94ab4e86-77f1-480b-86bb-326fc8852a0c']) {
        sh '''
          ssh root@139.144.118.178 -v
          echo "NHGI"
        '''
      }
    }
  }
    stage('build') {
      steps {
        sh 'docker build -t react -f Dockerfile.dev .'
      }
    }
    stage('test') {
      steps {
        sh 'docker run -e CI=true react npm run test'
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
      sshagent(credentials: ['94ab4e86-77f1-480b-86bb-326fc8852a0c']) {
        sh '''
          ssh root@139.144.118.178 -v -t -t "docker login -u nguyenduynghi2001 -p Nghi@#2001 && docker pull nguyenduynghi2001/dk-react && docker run --name react --rm -p 80:80 -d nguyenduynghi2001/dk-react"
        '''
        sh 'echo "Success"'
      }
    }
    }

  }
}
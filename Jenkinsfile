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
      sshagent(credentials: ['74e1554c-0070-4c0e-a33e-8dfd974df2a2']) {
        sh '''
          ssh -tt -o StrictHostKeyChecking=no root@139.144.118.178 -v
          echo $NGHI
        '''
      }
    }
  }
    // stage('build') {
    //   steps {
    //     sh 'docker build -t react -f Dockerfile.dev .'
    //   }
    // }
    // stage('test') {
    //   steps {
    //     sh 'docker run -e CI=true react npm run test'
    //   }
    // }
    // stage('push') {
    //   steps {
    //     sh 'docker login -u nguyenduynghi2001 -p Nghi@#2001'
    //     sh 'docker tag react nguyenduynghi2001/dk-react'
    //     sh 'docker push nguyenduynghi2001/dk-react'
    //     sh 'docker image rm nguyenduynghi2001/dk-react'
    //   }
    // }
    // stage('deploy') {
    //   steps {
    //     sh 'echo "Nghi"'
    //   }
    // }

  }
}
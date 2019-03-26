pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t juan-huarachi/docker-react -f Dockerfile.dev .'
      }
    }
    stage('Test') {
      steps {
        echo 'TEST'
        sh 'docker run juan-huarachi/docker-react  npm run test -- --coverage'
      }
    }
    stage('Deploy') {
      steps {
        echo 'DEPLOY'
      }
    }
  }
}
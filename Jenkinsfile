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
  post {
    always {
      echo 'I will always say Hello again!'

      emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
        recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
        subject: "Jenkins Build ${currentBuild.currentResult}"
        
    }
  }
}
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t img-docker-node-example .'
      }
    }

  }
}
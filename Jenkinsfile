pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t img-docker-node-example .'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'test-devops', description: 'test-description', title: 'titre-test')
      }
    }

  }
}
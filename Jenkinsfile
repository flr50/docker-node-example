pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'start build'
        sh 'docker build -t img-docker-node-example .'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUP-BUILD', description: 'BUILD SUCCESS', title: 'INFO BUILD')
        echo 'end build'
      }
    }

    stage('Scan') {
      steps {
        echo 'start scan'
        sh 'docker run -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest image img-docker-node-example'
        echo 'end scan'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', title: 'INFO SCAN', description: 'SCAN SUCCESS', customUsername: 'SUP-SCAN')
      }
    }

    stage('Deploy') {
      steps {
        echo 'start deploy'
      }
    }

  }
}
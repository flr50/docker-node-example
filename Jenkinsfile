pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'start build'
        discordSend(customUsername: 'SUPERVISION_JENKINS', description: 'BUILD_START', title: 'INFO_BUILD', webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6')
        sh 'docker build -t img-docker-node-example .'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'BUILD_END', title: 'INFO_BUILD')
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'BUILD_SUCCESS', title: 'INFO_BUILD')
        echo 'end build'
      }
    }

    stage('Scan') {
      steps {
        echo 'start scan'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'SCAN_START', title: 'INFO_SCAN')
        sh 'docker run -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest image img-docker-node-example'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'SCAN_END', title: 'INFO_SCAN')
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', title: 'INFO_SCAN', description: 'SCAN_SUCCESS', customUsername: 'SUPERVISION_JENKINS')
        echo 'end scan'
      }
    }

    stage('Deploy') {
      steps {
        echo 'start deploy'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'DEPLOY_START', title: 'INFO_DEPLOY')
        sh 'docker run --name cnt-docker-node-exmaple -d -p 8000:80 img-docker-node-example'
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'DEPLOY_END', title: 'INFO_DEPLOY')
        discordSend(webhookURL: 'https://discord.com/api/webhooks/1174361941305741352/-zar7V61kIeLtcG6XGEj464IRm4jLD-kq0c0_AD0WJKczil3wRJsNKR-70iGP8-vmYW6', customUsername: 'SUPERVISION_JENKINS', description: 'DEPLOY_SUCCES', title: 'INFO_DEPLOY')
        echo 'end deploy'
      }
    }

  }
}

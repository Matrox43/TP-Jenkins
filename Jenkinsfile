pipeline {
  agent any
  stages {
    stage('clôner le dépôt') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Matrox43/TP-Jenkins.git']]])
      }
    }

    stage('Construire l\'image') {
      steps {
        script {
          docker.build('test-image-jenkins')
        }

      }
    }

    stage('Analyser l\'image avec Trivy') {
      steps {
        sh 'docker run -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest image test-image-jenkins'
      }
    }

    stage('D�ploiement') {
      when {
        expression {
          currentBuild.resultIsBetterOrEqualTo('SUCCESS')
        }

      }
      steps {
        script {
          def container = docker.image('test-image-jenkins').run("--name test-auto-jenkins -p 8000:80 -d")
        }

      }
    }

  }
  post {
    always {
      script {
        discordSend(
          description: "Le build a ${currentBuild.result}",
          result: currentBuild.result,
          title: env.JOB_NAME,
          webhookURL: "https://discord.com/api/webhooks/1174692530676305990/ZckPjJq6UAgflOp5FG_GdYldWEfwkSG9jp7ty1bXykKAD7-ZnJG-DFO88-B4ZG0L9ed-" )
        }

      }

    }
  }
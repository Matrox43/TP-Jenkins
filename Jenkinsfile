pipeline {
  agent any
  stages {
    stage('clÃ´ner le dÃ©pÃ´t') {
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

    stage('Déploiement') {
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

    stage('Suppresion Image') {
      steps {
        sh '''docker ps -a
'''
        sleep 90
        sh 'docker rm --force test-auto-jenkins'
        sh 'docker ps -a'
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
          webhookURL: "https://discord.com/api/webhooks/1174693509517815909/PnME1Zumcp-KkNP4_WZwOSpOlgFZy7Fm5DR6NxyqXMFA-IMwHWR4mX26TFkA2xzETv1g")
        }

      }

    }
  }
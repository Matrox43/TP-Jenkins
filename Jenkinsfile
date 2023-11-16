pipeline {
  agent any
  stages {
    stage('clôner le dépôt') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Matrox43/TP-Jenkins']]])
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

  }
}
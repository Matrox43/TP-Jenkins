pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          docker.build ('https://github.com/Matrox43/TP-Jenkins/blob/main/Dockerfile')
        }

      }
    }

  }
}
pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          sh 'docker buildx build --progress=plain --load -t https://github.com/Matrox43/TP-Jenkins/Dockerfile'
        }

      }
    }

  }
}
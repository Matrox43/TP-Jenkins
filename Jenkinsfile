pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          sh 'docker buildx build --progress=plain --load -t "Dockerfile" .'
        }

      }
    }

  }
}
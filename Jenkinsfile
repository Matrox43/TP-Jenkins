pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        echo 'Test'
        sleep 30
        echo 'Fin de test'
      }
    }

    stage('Build') {
      steps {
        echo 'Start build Stage'
        sleep 20
        echo 'End Build Stage'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Start Deploy Stage'
        sleep 20
        echo 'End Deploy Stage'
      }
    }

  }
}
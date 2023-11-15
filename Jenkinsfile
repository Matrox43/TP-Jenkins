pipeline {
  agent any
  stages {
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test'
            sleep 30
            echo 'Fin de test'
          }
        }

        stage('Clone Repository') {
          steps {
            sh 'git clone https://github.com/Matrox43/TP-Jenkins'
          }
        }

        stage('Catch error Repository') {
          steps {
            warnError(message: 'Repository non trouvé')
          }
        }

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
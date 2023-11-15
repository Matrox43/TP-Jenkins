pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        script {
          def CLONE = sh(script: 'git clone https://github.com/Matrox43/TP-Jenkins', returnStatus: true)
          if(CLONE!= 0){ error('Failed to clone repository')
        }
      }

    }
  }

}
}
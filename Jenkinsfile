pipeline {
  agent any
  stages {
    stage('Construire image') {
      steps {
        script {
          try {
            dir('Jenkins') {
              sh 'docker build -t docker-image:latest .'
            }
          } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Erreur lors de la construction : ${e.message}"
          }
        }

      }
    }

  }
}
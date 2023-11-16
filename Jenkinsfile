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
  post {
    success {
      emailext(subject: 'Build Jenkins réussi', body: 'Le build a réussi.', to: 'jeancoignard@gmail.com')
    }

    failure {
      emailext(subject: 'Échec du Build Jenkins', body: 'Le Jenkins a échoué.', to: 'jeancoignard@gmail.com')
    }

  }
}
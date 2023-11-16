pipeline {
  agent any
  stages {
    stage('Construire image') {
      steps {
        script {
          try {
            dir('Jenkins') {
              sh 'sudo systemctl start docker '
              sh 'docker build -t docker-image .'
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
      emailext(body: 'Le build a réussi.', subject: 'Succès du build', to: 'jeancoignard@gmail.com')
    }

    failure {
      emailext(body: 'Le build a échoué.', subject: 'Échec du build', to: 'jeancoignard@gmail.com')
    }

  }
}
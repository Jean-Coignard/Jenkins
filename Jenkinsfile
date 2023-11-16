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
      emailext(subject: 'Build Jenkins r�ussi', body: 'Le build a r�ussi.', to: 'jeancoignard@gmail.com')
    }

    failure {
      emailext(subject: '�chec du Build Jenkins', body: 'Le Jenkins a �chou�.', to: 'jeancoignard@gmail.com')
    }

  }
}
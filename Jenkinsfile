pipeline {
  agent any
  stages {
    stage('Construire image') {
      steps {
        script {
          try {
            dir('Jenkins') {
              sh 'docker run -v /var/run/docker.sock:/var/run/docker.sock -v $(pwd):/workspace docker build -t docker-image .'
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
      emailext(body: 'Le build a r�ussi.', subject: 'Succ�s du build', to: 'jeancoignard@gmail.com')
    }

    failure {
      emailext(body: 'Le build a �chou�.', subject: '�chec du build', to: 'jeancoignard@gmail.com')
    }

  }
}
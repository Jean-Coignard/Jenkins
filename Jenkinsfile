pipeline {
  agent any
  stages {
    stage('Depot') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/Jean-Coignard/Jenkins.git']]])
      }
    }

    stage('Construire') {
      steps {
        script {
          try {
            dir('Jenkins') {
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
}
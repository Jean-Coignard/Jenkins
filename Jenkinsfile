pipeline {
  agent any
  stages {
    stage('Depot') {
      steps {
        script {
          try {
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Jean-Coignard/Jenkins.git']]])
          } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Erreur lors du clonage du dépôt : ${e.getMessage()}"
          }
        }

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
            error "Erreur lors de la construction : ${e.getMessage()}"
          }
        }

      }
    }

  }
}
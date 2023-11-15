pipeline {
  agent any
  stages {
    stage('Depot') {
      steps {
        script {
          try {
            sh 'git clone https://github.com/Jean-Coignard/Jenkins.git'
          } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Erreur lors du clonage du depot : ${e.message}"
          }
        }

      }
    }

    stage('Construire image') {
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
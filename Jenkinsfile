pipeline {
  agent any
  stages {
    stage('Cloner le Dépôt') {
      steps {
        script {
          try {
            // Cloner le dépôt GitHub
            git 'https://github.com/Jean-Coignard/Jenkins.git'
          } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Erreur lors du clonage du dépôt : ${e.message}"
          }
        }

      }
    }

  }
}
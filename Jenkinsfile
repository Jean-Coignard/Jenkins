pipeline {
  agent any
  stages {
    stage('Cloner le D�p�t') {
      steps {
        script {
          try {
            // Cloner le d�p�t GitHub
            git 'https://github.com/Jean-Coignard/Jenkins.git'
          } catch (Exception e) {
            currentBuild.result = 'FAILURE'
            error "Erreur lors du clonage du d�p�t : ${e.message}"
          }
        }

      }
    }

  }
}
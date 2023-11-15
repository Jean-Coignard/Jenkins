pipeline {
  agent any
  stages {
    stage('Depôt') {
      steps {
        sh 'git clone https://github.com/Jean-Coignard/Jenkins.git'
      }
    }

    stage('Construction Image') {
      steps {
        sh '''cd C:\\Users\\jeanc\\Downloads
docker build -t docker_tp:latest .'''
      }
    }

  }
}
pipeline {
  agent any
  stages {
    stage('Depot') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/Jean-Coignard/Jenkins.git']]])
      }
    }

  }
}
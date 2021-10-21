pipeline {
  agent any

  stages {
    stage('Build image') {
      steps {
        echo 'Building image'
        sh 'docker build -t testImage1 .'
      }
    }
    stage('Test image') {
      steps {
        echo 'Testing image'
        snykSecurity(
          snykInstallation: 'snyk1',
          snykTokenId: 'snyk'
        ) {
          sh 'snyk container test testImage1'
        }
      }
    }
  }
}
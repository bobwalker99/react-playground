pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'yarn install', returnStatus: true, returnStdout: true)
      }
    }
  }
}
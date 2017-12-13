pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'yarn --verbose install', returnStatus: true, returnStdout: true)
      }
    }
  }
}
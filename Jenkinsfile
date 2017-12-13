pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'npm install', returnStatus: true, returnStdout: true)
      }
    }
  }
}
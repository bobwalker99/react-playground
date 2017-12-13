pipeline {
  agent any
  environment {
    CI = 'true'
  }
  stages {
    stage('Build') {
      steps {
        bat(script: 'yarn install', returnStatus: true, returnStdout: true)
      }
    }
  }
}

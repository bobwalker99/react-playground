pipeline {
  agent any
  environment {
    CI = 'true'
  }
  stages {
    stage('Build') {
      steps {
        bat(script: 'yarn --verbose install', returnStatus: true, returnStdout: true)
      }
    }
  }
}

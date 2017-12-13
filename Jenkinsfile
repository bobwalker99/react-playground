pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            bat(script: 'yarn --verbose install', returnStatus: true, returnStdout: true)
          }
        }
        stage('Test') {
          steps {
            bat(script: 'yarn flow', returnStatus: true, returnStdout: true)
          }
        }
      }
    }
  }
}
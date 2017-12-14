pipeline {
  agent any
  stages {
    stage('Setup') {
      steps {
        bat(script: 'yarn --verbose install', returnStatus: true, returnStdout: true)
      }
    }
    stage('Quality') {
      parallel {
        stage('Build') {
          steps {
            bat(script: 'yarn build', returnStatus: true, returnStdout: true)
          }
        }
        stage('Test') {
          steps {
            bat(script: 'yarn test', returnStatus: true, returnStdout: true)
          }
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}
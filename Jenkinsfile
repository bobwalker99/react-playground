pipeline {
  agent any
  environment {
    CI = 'true'
  }
  stages {
    stage('Build') {
      parallel {
        stage('Setup') {
          steps {
            bat(script: 'yarn --verbose install', returnStatus: true, returnStdout: true)
          }
        }
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
}

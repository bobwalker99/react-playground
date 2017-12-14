pipeline {
  agent any
  stages {
    stage('Setup') {
      steps {
        sh(script: 'yarn --verbose install', returnStatus: true)
      }
    }
    stage('Quality') {
      parallel {
        stage('Build') {
          steps {
            sh(script: 'yarn build', returnStatus: true)
          }
        }
        stage('Test') {
          steps {
            sh(script: 'yarn test', returnStatus: true)
          }
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}

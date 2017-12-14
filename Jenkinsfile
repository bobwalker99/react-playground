pipeline {
  agent any
  stages {
    stage('Setup') {
      steps {
        bat(script: 'yarn --verbose install', returnStatus: true)
      }
    }
    stage('Quality') {
      parallel {
        stage('Build') {
          steps {
            if (isUnix()) {
              sh(script: 'yarn build', returnStatus: true)
            }
            else {
              bat(script: 'yarn build', returnStatus: true)
            }
          }
        }
        stage('Test') {
          steps {
            if (isUnix()) {
              sh(script: 'yarn test', returnStatus: true)
            }
            else {
              bat(script: 'yarn test', returnStatus: true)
            }
          }
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}

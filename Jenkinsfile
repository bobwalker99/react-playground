pipeline {
  agent {
      docker {
          image 'node:9-alpine'
          args '-p 3000:3000'
      }
  }
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

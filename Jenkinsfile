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
            parallel(
              linux: {
                sh(script: 'yarn build', returnStatus: true)
              },
              windows: {
                bat(script: 'yarn build', returnStatus: true)
              },
              failFast: false)
           }
        }
        stage('Test') {
          steps {
            parallel(
                linux: {
                    sh(script: 'yarn test', returnStatus: true)
                },
                windows: {
                    bat(script: 'yarn test', returnStatus: true)
                }
            failFast=false)
          }
        }
      }
    }
  }
  environment {
    CI = 'true'
  }
}

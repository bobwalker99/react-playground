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
          parallel {
            stage('Build On Windows') {
              agent {
                label "windows"
              }
              steps {
                bat(script: 'yarn build', returnStatus: true)
              }
            }
            stage('Test On Linux') {
              agent {
                label "linux"
              }
              steps {
                sh(script: 'yarn build', returnStatus: true)
              }
            }
          }
        }
        stage('Test') {
          parallel {
            stage('Test On Windows') {
              agent {
                label "windows"
              }
              steps {
                bat(script: 'yarn test', returnStatus: true)
              }
            }
            stage('Test On Linux') {
              agent {
                label "linux"
              }
              steps {
                sh(script: 'yarn test', returnStatus: true)
              }
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

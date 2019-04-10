pipeline {
  agent {
    label 'maven'
  }
  stages {
    stage('Maven clean') {
      steps {
        sh 'mvn clean'
      }
    }
    stage('Maven install') {
      steps {
        withMaven() {
          sh 'mvn install -U'
        }
      }
    }
  }
  triggers {
    pollSCM('H/15 9-18 * * 1-5')
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
    timestamps()
  }
}
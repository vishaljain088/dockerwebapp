pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t vishaljain088/java-web-app:latest .'
      }
    }
    stage('Scan') {
      steps {
        sh 'trivy vishaljain088/java-web-app:latest'
      }
    }
  }
}

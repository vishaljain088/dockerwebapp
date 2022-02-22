pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Clone Repository') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t vishaljain088/dockerwebapp .'
      }
    }
    stage('Scan') {
      steps {
        sh 'docker run ghcr.io/aquasecurity/trivy:latest image vishaljain088/dockerwebapp'
      }
    }
  }
}

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
        sh 'docker run ghcr.io/aquasecurity/trivy:latest image -f json -o scanning.json vishaljain088/dockerwebapp'
      }
    }
    stage("Email Notification"){
      steps {
        emailext (attachmentsPattern: 'scanning.json', subject: "Trivy Scanning", body: '''${SCRIPT, template="groovy-html.template"}''', mimeType: 'text/html', to: 'jenkinsbyjain@gmail.com')
      }
    }
  }
}

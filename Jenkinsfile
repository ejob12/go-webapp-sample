pipeline {
  agent any
  stages {
    stage('dev') {
      steps {
        sh 'go test ./...'
      }
    }
    stage('build') {
      steps {
        script {
          docker.build("adminturneddevops/go-webapp-sample")
        }
      }
    }
  }
}
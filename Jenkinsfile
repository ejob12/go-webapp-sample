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
    stage('deploy') {
      steps {
        sh "docker run -p 8090:8000 -d adminturneddevops/go-webapp-sample"
      }
    }
  }
}
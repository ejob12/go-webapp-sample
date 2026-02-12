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
          docker.build("ejob12/go-webapp-sample")
        }
      }
    }
    stage('push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
            docker.image("ejob12/go-webapp-sample").push()
          }
        }
      }
    }
    stage('deploy') {
      steps {
        sh "docker run -p 8090:8000 -d ejob12/go-webapp-sample"
      }
    }
  }
}
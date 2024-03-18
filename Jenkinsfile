pipeline {
  agent any
  stages {
    stage('Build and Push Image') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'docker-pat') {
            docker.build("parandzem/front")
            docker.image("parandzem/front").push()
          }
        }
      }
    }
  }
}

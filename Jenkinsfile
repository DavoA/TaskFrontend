pipeline {
  agent any
  triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'myHash', value: '$.after'],
            ],
            token: 'front'
        )
  }
  stages {
    stage('Build Image') {
      steps {
        script {
          docker.build("parandzem/front")
          }
        }
      }
    }
    stage('Give Tag and Push Image') {
      steps {
        def mytag = env.myHash.substring(0, 7)
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'docker-pat') {
            docker.build("parandzem/front")
            docker.image("parandzem/front").push(mytag)
        }
      }
    }
  }
}

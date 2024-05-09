pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building application'
        sh 'chmod +x scripts/build.sh'
        sh 'scripts/build.sh'
        sh 'sudo docker build -t mydockerfile:1.0 .'
        script {
          withCredentials([usernamePassword(credentialsId: 'dockerhub_id', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
            sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
            sh "docker push matmoz/my_dockerhub:1.0"
          }
        }

        echo 'Building finished'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing build'
        sh 'chmod +x scripts/test.sh'
        sh 'scripts/test.sh'
        echo 'Testing finished'
      }
    }

  }
}
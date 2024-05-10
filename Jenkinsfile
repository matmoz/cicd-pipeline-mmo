pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building application'
        sh 'chmod +x scripts/build.sh'
        sh 'scripts/build.sh'
        sh 'sudo docker build -t my_dockerhub:1.0 .'
        script {
          withCredentials([usernamePassword(credentialsId: 'dockerhub_id', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
            sh "echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin"
            sh "docker push my_dockerhub:1.0"
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
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building application'
        sh 'chmod +x scripts/build.sh'
        sh 'scripts/build.sh'
        sh 'sudo docker build -t mydockerfile:1.0 .'
        sh 'docker.withRegistry( \'\', \'dockerhub_id\'){dockerImage.push()}'
        sh 'docker push matmoz/mydockerfile:1.0'
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
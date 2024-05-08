pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building application'
        sh 'chmod +x scripts/build.sh'
        sh 'scripts/build.sh'
        echo 'Building finished'
        sh 'sudo docker build -t Dockerfile:01 .'
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
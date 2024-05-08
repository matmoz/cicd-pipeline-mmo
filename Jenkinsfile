pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building application'
        sh 'chmod +x scripts/build.sh'
        sh 'scripts/build.sh'
        echo 'Finishing build'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing app'
      }
    }

  }
}
pipeline {
  agent none
  stages {
    stage('Front-end') {
      agent {
        docker { image 'busybox' }
      }
      steps {
        sh 'cat /etc/os-release'
      }
    }
  }
}

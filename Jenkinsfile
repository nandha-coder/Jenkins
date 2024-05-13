pipeline {
  agent none
  stages {
    stage('Back-end') {
      agent {
        docker { image 'nginx' }
      }
      steps {
        sh 'cat /etc/os-release'
      }
    }
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

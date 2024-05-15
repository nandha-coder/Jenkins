pipeline {
  agent {
        docker { image 'busybox' }
		}
  stages {
    stage('Front-end') {
      steps {
        sh 'cat /etc/os-release'
      }
    }
  }
}

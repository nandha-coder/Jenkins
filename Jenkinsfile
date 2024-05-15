pipeline {
  agent {
        docker { 
		image 'busybox'
	        args  'sleep 10000000'}
		}
  stages {
    stage('Front-end') {
      steps {
        sh 'cat /etc/os-release'
      }
    }
  }
}

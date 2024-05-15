pipeline {
  agent {
        docker { 
		image 'busybox'
	        label 'latest'
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

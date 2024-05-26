pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'maven'
    }
    stages {
        stage('GIT Checkout') {
            steps {
                git 'https://github.com/jaiswaladi246/secretsanta-generator.git'
            }
        }		
	    stage('Code Build Checkout') {
            steps {
                sh 'mvn clean package'
            }
        }
        }
}

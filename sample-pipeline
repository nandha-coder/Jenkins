pipeline {
    agent any
    tools{
        jdk 'jdk17'
        maven 'maven'
// tESTING
    }
    environment{
        DOCKER_IMAGE= "nandyuvi/9043:${BUILD_NUMBER}"
    }
    stages {
        stage('GIT Checkout') {
            steps {
                git 'https://github.com/nandha-coder/secretsanta-nandha.git'
            }
        }		
	stage('Code Compile') {
            steps {
                sh 'echo ${BUILD_NUMBER} > abc.txt && mvn clean compile'
            }
        }
	stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
	stage('SonarQube Analysis') {
	     environment {
        	SONAR_URL = "http://64.227.184.243:9000"
      			}
            steps {
                withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_AUTH_TOKEN')]) {
    		sh 'mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
		}
            }
        }
	stage('Code Build') {
            steps {
                sh 'mvn clean package'
            }
        }
	stage('Image Build') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }	
	stage('Image Push') {
            steps {
		script {
		withDockerRegistry(credentialsId: 'docker-username-password', toolName: 'docker') {
		sh 'docker push ${DOCKER_IMAGE}'
}

		}
            }
        }
	}
}

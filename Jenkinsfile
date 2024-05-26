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
	      environment {
				DOCKER_IMAGE = "nandyuvi/9043:${BUILD_NUMBER}"
				}
            steps {
                sh 'docker build -t ${DOCKER_IMAGE}' .
            }
        }
	stage('Image Push') {
	      environment {
					DOCKER_IMAGE = "nandyuvi/9043:${BUILD_NUMBER}"
				}
            steps {
                sh "docker push ${DOCKER_IMAGE}"
            }
        }		
        }
}

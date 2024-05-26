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
                sh 'mvn clean compile'
            }
        }
	stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
        }
	stage('Code Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        }
}

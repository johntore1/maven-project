pipeline {
    agent any
 
    stages {
		stage('scm checkout'){
			steps{
			git 'https://github.com/johntore1/maven-project.git'
			}
		}
		stage('compile source code'){
			steps{
			withMaven (maven: 'local_maven'){
			sh 'mvn compile'}
			}
			}
		stage('test'){
			steps{
		withMaven(maven : 'local_maven') {
			sh 'mvn test'
			}
			}
		}		
	
		stage('build and sonar analysis'){
			steps{
			withSonarQubeEnv('kuchbi') {
   withMaven(maven : 'local_maven') {
			sh 'mvn clean package sonar:sonar'
			}
}
			}
		}
		
		}
       
    }

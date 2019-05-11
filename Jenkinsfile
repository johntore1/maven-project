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
		
		stage('package'){
			steps{
		withMaven(maven : 'local_maven') {
			sh 'mvn package'
			}
			}
		}
		stage('install'){
			steps{
		withMaven(maven : 'local_maven') {
			sh 'mvn install'
			}
			}
		}
       stage('deploy to tomcat'){
			steps{
			sshagent(['dcda5da0-50df-4b50-8609-fdde21c2e396']) {
			sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@13.57.37.49:/var/lib/tomcat/webapps' 
		}
			
			}
			}
    }
}

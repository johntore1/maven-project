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
       
    }
}

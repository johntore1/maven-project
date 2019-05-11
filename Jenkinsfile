pipeline {
    any agent

    stages {
		stage('scm checkout'){
			git 'https://github.com/johntore1/maven-project.git'
		}
		stage('compile source code'){
			steps{
			withMaven (maven: 'local_maven'){
			sh 'mvn compile'}
			}
			}
		stage('test'){
		withMaven(maven : 'local_maven') {
			sh 'mvn test'
			}
		}
		
		stage('package'){
		withMaven(maven : 'local_maven') {
			sh 'mvn package'
			}
		}
		stage('install'){
		withMaven(maven : 'local_maven') {
			sh 'mvn install'
			}
		}
       
    }
}

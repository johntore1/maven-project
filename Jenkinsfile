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
		
		stage("build & SonarQube analysis") {
              steps{
             // script {
          // requires SonarQube Scanner 2.8+
          //scannerHome = tool 'sonarscanner'
       // }
        withSonarQubeEnv('SonarQube Scanner') {
		withMaven(maven:'Maven 3.5'){
          sh "${scannerHome}/bin/sonar-scanner"
	}
        }
            }
          }
		
		}
       
    }

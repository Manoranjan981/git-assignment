pipeline {
	agent any
	tools {
		maven 'Maven_3.8.7'
	}
	
	stages {
		stage('Get_Code') {
			steps {
				git branch: 'main',
				url: 'https://github.com/Manoranjan981/git-assignment.git'
			}
		}
		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
		}
		stage('Deploy') {
			steps {
				sshagent(['ssh-server-agent']) {
					sh 'scp -o StrictHostKeyChecking=no target/Maven-webapp.war ec2-user@43.205.99.217:/home/ec2-user/apache-tomcat-9.0.70/webapps'
				}
			}
		}
	}
}

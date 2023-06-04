pipeline {
	agent any
	tools {
		maven 'Maven 3.9.2'
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
				//sshagent(['ssh-server-agent']) {
				//	sh 'scp -o StrictHostKeyChecking=no target/Maven-webapp.war ec2-user@13.233.99.192:/home/ec2-user/apache-tomcat-11.0.0-M6/webapps'
				//}
				sh 'cp target/Maven-webapp.war /home/ec2-user/apache-tomcat-11.0.0-M6/webapps'
			}
		}
	}
}

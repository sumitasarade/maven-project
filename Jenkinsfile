pipeline{
agent any
stages{
	stage('clone repository'){
		steps('clone '){
		git 'https://github.com/sumitasarade/maven-project.git'
		}
	}
	stage(' compile'){
		steps('compile'){
		withMaven(jdk: 'JAVA_HOME', maven: 'maven') {
				sh 'mvn clean compile'
			}
		}
	}
	stage(test){
		steps('test'){
		}
	}
	stage('package'){
		steps('package'){
		withMaven(jdk: 'JAVA_HOME', maven: 'maven') {
				sh 'mvn package'
			}
		}
	}
	stage('deploy to tomcat'){
		steps('tomcat'){
		sshagent(['tomcat']) {
			sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@13.235.99.177:/var/lib/tomcat/webapps
			}
		}
	}
}
}

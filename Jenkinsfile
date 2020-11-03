pipeline{
	agent any
	stages{
		stage('Clone Repo'){
			steps('Cloning Repo'){
				git 'https://github.com/sumitasarade/maven-project.git'
			}
		}
		stage('Compile'){
			steps('Compiling') {
				withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
					sh 'mvn clean compile'
				}
			}
		}
		stage('Test'){
			steps('Testing') {
				withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
					sh 'mvn test'
				}
			}
		}
		stage('Package'){
			steps('Packaging') {
				withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
					sh 'mvn package'
				}
			}
		}
		stage('Install'){
			steps('Installing') {
				withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
					sh 'mvn install'
				}
			}
		}
		stage('Verify'){
			steps('Verifying') {
				withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') {
					sh 'mvn verify'
				}
			}
		}
					stage ('ssh tomcat') {
				       steps {
						sshPublisher(publishers: [sshPublisherDesc(configName: 'Tomcat', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/var/lib/tomcat/webapps', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
				       }	       
			}
		stage('Deploy to Tomcat'){
			steps('Deploying'){
				sshagent(['54.80.207.230']) {
					sh 'scp -o StrictHostKeyChecking=yes */target/*.war ec2-user@54.80.207.230:/var/lib/tomcat/webapps' 
				}
			}
		}
	}
}

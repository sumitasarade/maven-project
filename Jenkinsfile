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
	}
}

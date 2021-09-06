pipeline {
	agent any
	tools {
		maven 'maven3'
	}
	stages{
		stage('Build'){
			steps{
				sh script: 'mvn clean package'
			}
		}
		stage('Upload Artifact To Nexus'){
			steps{
				nexusArtifactUploader artifacts: [
					[
						artifactId: 'simple-app', 
						classifier: '', 
						file: 'target/simple-app-1.0.0.war', 
						type: 'war'
					]
				], 
				credentialsId: 'nexus3', 
				groupId: 'in.javahome', 
				nexusUrl: '172.31.9.220:8081', 
				nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: 'http://18.118.37.25:8081/repository/simpleapp-release/', 
				version: '1.0.0'
			}
		}
	}
}
// this is a single line comment

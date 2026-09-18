pipeline{
	agent{
		label 'worker'
	}
	tools{
		maven 'maven'
	}
	environment{
		aws_creds = credentials('aws-cred')
	}
	stages{
		stage('checkout'){
			steps{
				git 'https://github.com/avi-devopshub/student-management.git'
			}
		}
		stage('maven-build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('artifact-to-s3'){
			steps{
				sh 'aws s3 cp target/*.war s3://artifactory-554663574879-ap-south-1-an/artifact/student.war'
			}
		}
	}
}
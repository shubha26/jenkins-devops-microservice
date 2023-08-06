pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }

	environment{
		dockerHome = tool 'myMaven'
		mavenHome = tool 'myDocker'
		PATH="$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps{
				sh 'mvn --version'
				sh 'docker --version'
				echo "Build"
				echo "$PATH"
			}
		}
		stage('Compile') {
			steps{
				echo "Compile"
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps{
				echo "Test"
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps{
				echo "Integration Test"
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
	} 
	post {
		always {
			echo "I run always"
		}
		success {
			echo "I run on success"
		}
		failure {
			echo "I run on failure"
		}
	}
}

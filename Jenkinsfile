pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }

	environment{
		dockerHome = tool 'myMaven'
		mavenHome = tool 'myDocker'
		PATH="$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Build') {
			steps{
				sh 'mvn --version'
				sh 'docker --version'
				echo "Build"
				echo "$PATH"
			}
		}
		stage('Test') {
			steps{
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps{
				echo "Integration Test"
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

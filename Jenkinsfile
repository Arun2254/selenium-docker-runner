pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull ayellapu/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d selenium-hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up automation-practice webapp-security"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			// sh "sudo rm -rf output/"
		}
	}
}
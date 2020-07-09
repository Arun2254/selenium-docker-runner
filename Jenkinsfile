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
		
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "sudo rm -rf output/"
		}
	}
}
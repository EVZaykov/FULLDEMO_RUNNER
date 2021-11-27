pipeline{
	agent any
	stages {
		stage('Pull Latest Image'){
			steps{
				bat 'docker pull javaautotesting/zaikov:zaikov'
			}
		}
		stage('Start Grid'){
			steps {
				bat 'docker-compose up -d hub chrome'
				bat 'docker images'
			}
		}
		stage('Run Test'){
			steps{
				bat 'docker-compose up'
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat 'docker-compose down'
		}
	}
}
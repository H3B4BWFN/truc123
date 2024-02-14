pipeline {
    agent any

	stages {
		stage('SonarQube Analysis') {
			steps {
				withSonarQubeEnv(credentialsId: 'sqp_d217c0b289d7cddc106728c703c39145d6e8a5e3', installationName: 'SQserver') {
					sh './sonar-scanner-5.0.1.3006-linux/bin/sonar-scanner'
				}
			}
	        }

		stage('Quality Gate') {
			steps {
				script {
					def qg = waitForQualityGate()
					if(qg.status != 'OK') {
						error "Quality Gate failure : ${qg.status}"
					}
				}
			}
		}

	        stage('List files') {
			steps {
				sh 'ls -lah .'
			}
		}
	}
}

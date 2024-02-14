pipeline {
    agent any

	stages {
		stage('SonarQube Analysis') {
			steps {
				sh 'sonar-scanner'
			}
	        }

		stage('Quality Gate') {
			def qg = waitForQualityGate()
			if(qg.status != 'OK') {
				error "Quality Gate failure : ${qg.status}"
			}
		}

	        stage('List files') {
			steps {
				sh 'ls -lah .'
			}
		}
	}
}

pipeline {
    agent any

    stages {
        stage('SonarQube Analysis') {
            steps {
		withSonarQubeEnv('SQtoto') {
			sh 'sonar-scanner   -Dsonar.projectKey=toto   -Dsonar.sources=.   -Dsonar.host.url=http://localhost:9000   -Dsonar.token=sqp_d217c0b289d7cddc106728c703c39145d6e8a5e3'
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


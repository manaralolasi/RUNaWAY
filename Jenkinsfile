pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('manar-dockerhub-token')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t 7111418/runway:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push 7111418/runway:latest'
			}
		}

        stage ("Logout") {
            steps {
                sh 'docker logout'
            }
        }
	}
}
	 

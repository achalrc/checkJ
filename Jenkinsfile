pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerHub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'sudo docker build -t achalrc/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'sudo echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'sudo docker push achalrc/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'sudo docker logout'
		}
	}

}

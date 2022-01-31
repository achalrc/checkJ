pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerHub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t achalrc/nodeapp:latest .'
			}
		}
		
		stage('Publish image to Docker Hub') {
          
            		steps {
				withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
					sh  'docker push achalrc/nodeapp:latest'
				}
                  
          		}
        	}


	}


}

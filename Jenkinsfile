pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-nodejs')
	}

	stages {
	    
	        stage('gitclone') {

			steps {
				git 'https://github.com/abhay0177/Nodejs-project.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t abhays1/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push abhays1/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

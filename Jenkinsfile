pipeline {
	any agent 

	stages {
		stage('Clone') {
			steps {
				echo 'Getting latest codes'
			}
		}

		stage('Build Docker Image') {
			steps {
				sh 'docker build -t jenkinsweb .'
			}
		}

		stage('Deploy') {
			steps {
				sh '''
				docker stop mywebsite-container || true
				docker rm mywebsite-container || true

				docker run -d --name mywebsite-container -p 8080:80 jenkinsweb
				'''
			}
		}
	}
}	


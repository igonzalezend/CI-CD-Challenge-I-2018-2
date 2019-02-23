pipeline {

	environment{
		imageTag = 'cicdchallenge' + ":$BUILD_NUMBER"
		credentials = 'dockerhub'
	}

	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {                                 
					echo 'Preparing..'
					sh  'npm install'
				}                 
			}                 
			stage('Build') {                         
				steps {                                 
					echo 'Building..'

					script {
						dockerImage = docker.build imageTag
					}             
				}                 
			}                 
			stage('Test') {                         
				steps {                                 
					echo 'Testing...'
					script{
						dockerImage.inside {
							sh 'npm test'
						}
					}
				}                 
			}
			stage('push') {
				steps {
					echo 'pushing'
					script {
						docker.withRegistry('', credentials){
							dockerImage.push()
						}
					}
					sh 'docker rmi -f $imageTag'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 

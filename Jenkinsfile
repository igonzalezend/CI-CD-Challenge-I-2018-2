pipeline {

	environment{
		imageTag = "cicdchallenge" + env.BUILD_NUMBER
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
					sh ''' 
						docker build -t $imageTag:$BUILD_NUMBER .
					'''
					sh 'docker image ls'              
				}                 
			}                 
			stage('Test') {                         
				steps {                                 
					echo 'Testing...'
					sh 'docker run ${imageTag} npm test'
				}                 
			}
			stage('push') {
				steps {
					echo 'pushing'
					sh 'docker push igonzalezend/cicdchallenge'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 

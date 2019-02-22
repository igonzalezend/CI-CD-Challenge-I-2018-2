pipeline {
	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {                                 
					echo 'Preparing..'
					sh  'npm install'
					script {
						def imageTag = "cicdchallenge" + env.BUILD_NUMBER;
					}
				}                 
			}                 
			stage('Build') {                         
				steps {                                 
					echo 'Building..'
					sh '''
						docker rmi $(docker images --format '{{.Repository}}' | grep 'cicdchallenge')
						docker build -t ${imageTag} .
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
					sh 'docker push igonzalezend/cicdchallenge:${}'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 

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
						imageCount=$(docker images --format '{{.Repository}}' | grep 'cicdchallenge')
						if [[ -n imageCount ]]; then
							echo 'OK'
						else
							echo 'DONE'
						fi
						docker build --rm -t ${imageTag} .
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

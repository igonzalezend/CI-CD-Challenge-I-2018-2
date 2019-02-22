pipeline {
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
						imageName="challenge$BUILD_NUMBER"
						docker build -t $imageName .
					'''
					sh 'docker image ls'              
				}                 
			}                 
			stage('Test') {                         
				steps {                                 
					echo 'Testing...'
					sh 'docker run challenge npm test'
				}                 
			}
			stage('push') {
				steps {
					echo 'pushing'
					sh 'docker push igonzalezend/cicdchallenge:$BUILD_NUMBER'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 

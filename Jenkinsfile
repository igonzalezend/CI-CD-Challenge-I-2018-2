pipeline {
	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {                                 
					echo 'Preparing..'
					sh '''
						npm --prefix /Challenge install
						ls Challenge
					'''
				}                 
			}                 
			stage('Build') {                         
				steps {                                 
					echo 'Building..'                         
				}                 
			}                 
			stage('Test') {                         
				steps {                                 
					echo 'Testing...'                        
				}                 
			}
			stage('push') {
				steps {
					echo 'pushing'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 

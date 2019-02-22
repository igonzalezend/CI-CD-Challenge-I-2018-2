pipeline {
	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {                                 
					echo 'Preparing..'
					sh '''
						ls
						npm --prefix /Challenge install
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

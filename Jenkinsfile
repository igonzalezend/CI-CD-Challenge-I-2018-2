pipeline {

	environment{
		imageName = 'igonzalezend/cicdchallenge'
		imageTag = imageName + ":$BUILD_NUMBER"
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
				input("Deploy the image?")
				sh 'docker stop $imageName'
				sh 'docker rmi --force $(docker images -q)'
				script {
					docker.withRegistry('', credentials){
						sh 'docker pull $imageTag'
					}
				}
				sh 'docker run --rm -d -p 8000:8000 $imageTag'                                    					
			}                 
		}         
	} 
} 

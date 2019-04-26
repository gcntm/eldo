pipeline{
	environment{
	registry = "gcntm/eldo"
	registryCredential = "dockerhub"
	} 
	agent any
	stages{
		stage('Starting'){
		steps{
		sh 'echo starting...'
		}
	}
	stage('Checking Docker'){
	steps{
		sh 'sudo docker ps'
		}
	}
        stage('Build Images'){
        steps{
	script{
		dockerImage=docker.build registry + ":$BUILD_NUMBER"
                }
		}
        }

 stage('Push Image DockerHub'){
        steps{
        script{
                docker.withRegistry('',registryCredential){
		dockerImage.push()
	}
                }
                }
        }
	
   }
} 

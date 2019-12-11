pipeline {
    // master executor should be set to 0
    agent any
    stages {
		stage('Pull Image') {
            steps {
                //sh for MAC
                bat "docker pull valmondw/selenium-docker"
            }
        }
		stage('Start Hub') {
            steps {
                bat "docker-compose up -d hub chrome firefox"
            }
        }
		stage('Run Test') {
            steps {
                bat "docker-compose up bookflight-module_1 bookflight-module_2"
            }
        }
	}	
    post{
         always{
		     archiveArtifacts artifacts: 'output/**'
             bat "docker-compose down"
            }
    }    
}
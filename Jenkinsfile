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
		stage('Start Grid') {
            steps {
                bat "docker-compose up -d hub --scale chrome=2 --scale firefox=2"
            }
        }
		stage('Run Test') {
            steps {
                bat "docker-compose up bookflight-module_1 duckduck-module_1"
            }
        }
        stage('Stop Grid') {
            steps {
                bat "docker-compose down"
            }
        }
    }
}
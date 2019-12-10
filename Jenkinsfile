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
                bat "docker-compose up -d hub"
            }
        }
		stage('Start Nodes') {
            steps {
                bat "docker-compose up --scale chrome=4 --scale firefox=4"
            }
        }
		stage('Run Test') {
            steps {
                bat "docker-compose up bookflight-module_1 duckduck-module_1 --no-color"
            }
        }
        stage('Stop Grid') {
            steps {
                bat "docker-compose down"
            }
        }
    }
}
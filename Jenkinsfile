pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Run Test') {
            steps {
                //sh for MAC
                bat "docker-compose up --scale chrome=4 --scale firefox=4"
            }
        }
        stage('Bring Grid Down') {
            steps {
                //sh for MAC
                bat "docker-compose down"
            }
        }
    }
}
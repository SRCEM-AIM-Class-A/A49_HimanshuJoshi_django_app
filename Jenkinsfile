pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins/jenkins:lts"
        DOCKER_CREDENTIALS_ID = "f4b2b507697c0fe5b451cc8f8599c8428656d130cdb4fe17a852db210b98edf2"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/SRCEM-AIM-Class-A/A49_HimanshuJoshi_django_app'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        sh 'docker push $IMAGE_NAME'
                    }
                }
            }
        }
    }
}

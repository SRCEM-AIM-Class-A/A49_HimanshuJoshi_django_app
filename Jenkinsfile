pipeline {
    agent any

    environment {
        IMAGE_NAME = "himanshujoshi03/django_project:latest"
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
                    sh "docker build -t ${env.IMAGE_NAME} ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'f4b2b507697c0fe5b451cc8f8599c8428656d130cdb4fe17a852db210b98edf2', url: 'https://index.docker.io/v1/']) {
                        sh "docker push ${env.IMAGE_NAME}"
                    }
                }
            }
        }
    }
}

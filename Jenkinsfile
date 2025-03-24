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
                    def dockerImage = docker.build("${env.IMAGE_NAME}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'e5e36bb2-7377-4e4a-a2d7-f13e53fca6cc') {
                        docker.image("${env.IMAGE_NAME}").push()
                    }
                }
            }
        }
    }
}

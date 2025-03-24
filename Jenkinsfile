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
                    withDockerRegistry([credentialsId: 'e5e36bb2-7377-4e4a-a2d7-f13e53fca6cc', url: 'https://index.docker.io/v1/']) {
                        sh "docker push ${env.IMAGE_NAME}"
                    }
                }
            }
        }
    }
}

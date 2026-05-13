pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'Docker-credentials'
        IMAGE_NAME = 'pannu27/new_docker_image'
    }

    stages {

        stage('Build Java Application') {
            steps {
                bat 'javac prime.java'
            }
        }

        stage('Run Java Program') {
            steps {
                bat 'java prime'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'new_passwordd',
                    usernameVariable: 'sanghaviiiiiii',
                    passwordVariable: 'sang@1234'
                )]) {

                    bat 'echo %PASS% | docker login -u %USER% --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push %IMAGE_NAME%:latest'
            }
        }
    }
}

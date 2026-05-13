pipeline {
    agent any

    environment {
        IMAGE_NAME = 'pannu27/new_docker_image'
    }

    stages {

        stage('Build Java Application') {
            steps {
                bat 'javac hello.java'
            }
        }

        stage('Run Java Program') {
            steps {
                bat 'java hello'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'Docker-credentials',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {

                    bat 'docker login -u %USER% -p %PASS%'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME%:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push %IMAGE_NAME%:latest'
            }
        }
    }
}

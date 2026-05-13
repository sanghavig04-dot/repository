pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'new_passwordd '//give your credential name
        IMAGE_NAME = 'sanghaviiiiiii/new_docker_image'//give your image name
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

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME%:latest .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                credentialsId: 'new_passwordd',//give your credentials mentioned above
                usernameVariable: 'USER',
                passwordVariable: 'PASS')]) {

                    bat 'echo %PASS%| docker login -u %USER% --password-stdin'
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

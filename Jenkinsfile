pipeline {
    agent any
    environment {
        imageName = "hello-nginx"
    }
    stages {
        stage("Perpare"){
            steps {
                echo "Hello World";
            }
        }
        stage("check version"){
            steps {
                sh "docker --version"
            }
        }

        stage("push image") {
            steps {
                script{
                    docker.withRegistry('https://docker.io/v1', 'dockerhub-id'){
                        def image = docker.build("tag ${env.imageName}:1.${env.BUILD_NUMBER} nootiew/${env.imageName}:1.${env.BUILD_NUMBER}")
                        image.push()
                    }
                }
            }
        }
    }
}

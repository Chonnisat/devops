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
        stage("build image"){
            steps {
                sh "docker build -t ${env.imageName} ."
                sh "docker tag ${env.imageName} ${env.imageName}:1.${env.BUILD_NUMBER}"
            }
        }
        stage("push image") {
            steps {
                sh "docker login -u tiewwa_haha@hotmail.com -p 17428yBR"
                sh "docker push ${env.imageName}"
            }
        }
    }
}

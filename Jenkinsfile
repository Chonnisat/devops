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

        // stage("deploy") {
        //     steps{
        //         sshagent(['uat-server']){
        //             sh "echo XXXXX"
        //         }
        //     }
        // }

        stage("push image") {
            steps {
                script{
                    docker.withRegistry('https://registry.hub.docker.com/nootiew', 'dockerhub-id'){
                        def image = docker.build("${env.imageName}:1.${env.BUILD_NUMBER}")
                        image.push()
                    }
                }
            }
        }
    }
}

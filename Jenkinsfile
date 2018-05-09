pipeline {
    agent any
    environment {
        imageName = "nootiew/hello-nginx"
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
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-id'){
                        sh "docker build -t ${env.imageName}:1.${env.BUILD_NUMBER} ."
                        sh "docker tag ${env.imageName}:1.${env.BUILD_NUMBER} ${env.imageName}"
                        sh "docker push ${env.imageName}"
                    }
                }
            }
        }
    }
}

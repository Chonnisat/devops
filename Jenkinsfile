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

        stage('Deploy'){
            steps {
                sshagent(['uat-server']) {
                    sh "ssh -o StrictHostKeyChecking=no root@206.189.45.68 docker pull ${env.imageName}"
                }
            }
        }

        // stage("push image") {
        //     steps {
        //         script{
        //             docker.withRegistry('https://docker.io', 'dockerhub-id'){cker.build("${env.imageName}:1.${env.BUILD_NUMBER}")
        //                 image.push();
        //                 def image = do
        //                 // sh "docker build -t ${env.imageName}:1.${env.BUILD_NUMBER} ."
        //                 // sh "docker tag ${env.imageName} ${env.imageName}:1.${env.BUILD_NUMBER}"
        //                 // sh "docker push ${env.imageName}"
        //             }
        //         }
        //     }
        // }
    }
}

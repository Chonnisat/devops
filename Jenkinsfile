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

        stage("push image") {
            steps {
                script{
                    docker.withRegistry('https://docker.io', 'dockerhub-id'){
                        // docker.build("${env.imageName}:1.${env.BUILD_NUMBER}")
                        // image.push();
                        sh "docker build -t ${env.imageName}:1.${env.BUILD_NUMBER} ."
                        sh "docker tag ${env.imageName} ${env.imageName}:1.${env.BUILD_NUMBER}"
                        sh "docker push ${env.imageName}"
                    }
                }
            }
        }

        stage('Deploy'){
            steps {
                sshagent(['uat-server']) {
                    sh "ssh core@139.59.223.198 docker pull ${env.imageName}"
                }
            }
        }
    }
}

node {
    stage("Perpare"){
        echo "Hello World";
    }
    stage("check version"){
        sh "docker --version"
    }
    stage("build image"){
        steps {
            sh "docker build -t hello-nginx ."
        }
    }
}
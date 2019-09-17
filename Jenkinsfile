#!/usr/bin/env groovy

def container =  "${DOCKER_IMAGE}"

node {
  docker.image(container).inside{
    stage('Checkout'){
      git branch: "${params.BRANCH}", url: 'https://github.com/dyudin0821/pipeline-example-go.git'
    }
    stage('Build'){
      sh '''echo $GOPATH
export XDG_CACHE_HOME=/tmp/.cache
mkdir -p $GOPATH/src/github.com/rancher
ln -s `pwd` $GOPATH/src/github.com/rancher/pipeline-example-go
cd /go/src/github.com/rancher/pipeline-example-go
go build -o bin/hello-server'''
    }
    stage('Building image'){
      def customImage = docker.build("my-image:${env.BUILD_ID}")
    }
  }
}
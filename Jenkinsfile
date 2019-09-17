#!/usr/bin/env groovy

def container =  "${DOCKER_IMAGE}"

node {
  checkout([
    $class: 'GitSCM',
    branches: [[name: "*/${BRANCH}"]], 
    doGenerateSubmoduleConfigurations: false,
    submoduleCfg: [], 
    userRemoteConfigs: [[credentialsId: 'd82dba23-c4f0-40e2-9165-576f0d4f3cae', url: "https://github.com/dyudin0821/pipeline-example-go.git"]]
  ])
  docker.image(container).inside{
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
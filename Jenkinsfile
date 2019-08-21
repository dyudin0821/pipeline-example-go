pipeline {
  agent {
    docker {
      image 'golang:1.12'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''echo $GOPATH
mkdir -p $GOPATH/src/github.com/rancher
ln -s `pwd` $GOPATH/src/github.com/rancher/pipeline-example-go'''
      }
    }
  }
}
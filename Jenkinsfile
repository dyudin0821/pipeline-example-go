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
export XDG_CACHE_HOME=/tmp/.cache
mkdir -p $GOPATH/src/github.com/rancher
ln -s `pwd` $GOPATH/src/github.com/rancher/pipeline-example-go
cd /go/src/github.com/rancher/pipeline-example-go
go build -o bin/hello-server'''
      }
    }
    stage('Building image') {
      steps {
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }

      }
    }
  }
}
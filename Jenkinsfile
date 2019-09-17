#!/usr/bin/env groovy

def container =  "${DOCKER_IMAGE}"

 node{
   stage('Checkout'){
     checkout([$class: 'GitSCM', branches: [[name: "*/${BRANCH}"]], doGenerateSubmoduleConfigurations: false, submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'd82dba23-c4f0-40e2-9165-576f0d4f3cae', url: "https://github.com/dyudin0821/pipeline-example-go.git"]]])
   }
   stage("Test"){
     sh "ls -lah"
   }
 }
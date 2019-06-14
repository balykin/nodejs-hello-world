#!groovy
properties([disableConcurentBuilds()])
pipeline {
  agent { label 'UbuntuSlave01' }
  options { 
    buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
    timestamps()
  }
libraries {
 lib('lib-demo@stage') 
} 
  stages {
    stage('Git Checkout') {
        steps {
            git branch: 'stage',
            url: 'https://github.com/devopssoftermii/cryptorunIOS.git'
            sh "ls -lat"
            }
    stage ('build_image') {
        steps {
            sh "docker build . -t hellonode:1"
        }
    }
    stage ('demo') {
      agent {
        docker { image 'hellonode' }
      }
      steps {
        sh "node --version"
        sh "node index.js"
        }
    }    
  }
}

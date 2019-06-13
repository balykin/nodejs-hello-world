pipeline {
  agent { label 'UbuntuSlave01' }
libraries {
 lib('lib-demo@master') 
} 
  stages {
    stage ('dokerfile') {
        sh "touch dockerfile"
    }
    stage ('build image') {
        sh "docker build . -t getintodevops-hellonode:1"
    }
    stage ('demo') {
      agent {
        docker { image 'node:7-alpine' }
      }
      steps {
        sh "node --version"
        sh "node index.js"
        }
    }    
  }
}

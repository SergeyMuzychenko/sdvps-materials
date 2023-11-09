pipeline {
 agent any
 stages {
  stage('Git') {
   steps {
    git 'https://github.com/SergeyMuzychenko/sdvps-materials'
   }
  }
  stage('Test') {
   steps {
    sh '/usr/local/go/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t ubuntu:8082/hello-world:v$BUILD_NUMBER'
   }
  }
  stage('Push') {
   steps {
    sh 'docker login ubuntu:8082 -u admin --password-stdin admin && docker push ubuntu:8082/hello-world:v$BUILD_NUMBER && docker logout'   }
  }
 }
}

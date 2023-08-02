pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        sh 'cd /opt'
        sh 'git pull "https://github.com/Sivashree-J/task.git" '
      }
    }
    stage('Build') {
      steps {
        script{
        sh 'docker build -t dimage .'
        sh 'docker tag dimage:latest sivashree03/dapp:tagname'
        docker.withRegistry("", "DockerHub") {
        def image = docker.image("sivashree03/dapp:tagname");
          image.push()
      }
        } 
        }
    }
 
 
  }
}

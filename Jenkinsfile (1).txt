pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        sh 'cd /opt'
        sh 'git pull "https://github.com/TharunMg06/app.git" '
      }
    }
    stage('Build') {
      steps {
        script{
        sh 'docker build -t vmi .'
        sh 'docker tag vmi:latest nandha13/demo:tagname'
        docker.withRegistry("", "DockerHub") {
        def image = docker.image("nandha13/demo:tagname");
          image.push()
      }
        } 
        }
    }
 
 
  }
}

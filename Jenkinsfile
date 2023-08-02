pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        sh 'cd /opt'
        sh 'git pull "https://github.com/preethi-s-00/dotnetapp-task.git" '
      }
    }
    stage('Build') {
      steps {
        script{
        sh 'docker build -t dotnet-image .'
        sh 'docker tag dotnet-image:latest preethi00/dotnetapp:tagname'
        docker.withRegistry("", "DockerHub") {
        def image = docker.image("preethi00/dotnetapp:tagname");
          image.push()
      }
        } 
        }
    }
 
 
  }
}

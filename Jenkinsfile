@Library ("mylibs") _
pipeline{
  agent any
  tools {
  maven 'maven2'
}
  stages{
    stage("maven build"){
      steps{
        sh "mvn clean package"
      }
    }
    stage("deploy to dev"){
      steps{
        tomcatdev("tomcat","ec2-user","172.31.12.240")
      }
    }
  }
}

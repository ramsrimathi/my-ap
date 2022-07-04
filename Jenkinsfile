pipeline{
  agent any
  tools {
  maven 'maven2'
}
  stages{
//    stage("git checkout"){
//      steps{
//        git credentialsId: 'ramsrimathi', url: 'https://github.com/ramsrimathi/my-ap',branch:"master"
//      }
//    }
    stage("maven build"){
      steps{
        sh "mvn clean package"
      }
    }
    stage("deploy to dev"){
      steps{
        sshagent (['tomcat']) {
        sh "mv target/*.war target/webapp.war"
        sh "scp -o StrictHostKeyChecking=no target/webapp.war ec2-user@172.31.12.240:/opt/tomcat9/webapps"
        sh "ssh ec2-user@172.31.12.240 /opt/tomcat9/bin/shutdown.sh"
        sh "ssh ec2-user@172.31.12.240 /opt/tomcat9/bin/startup.sh"
        }
      }
    }
  }
}

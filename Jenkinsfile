pipeline {
  agent any
  tools {
  maven 'maven2'
}
    stages{
 //   stage("SCM Checkout"){
//     steps{
//      git credentialsId: 'ramsrimathi', url: 'https://github.com/ramsrimathi/my-ap',branch: "master"
//     }
//   }
    stage("maven Build"){
      steps{
        sh "mvn clean package"
      }
    }
      stage("Deploy To Dev"){
       steps{
        sshagent(['tomcat']) {
          sh "mv taerget/*.war target/webapp.war"
          sh "SCP target/myweb.war -o StrictHostKeyChecking=no  ec2-user@172.31.12.240:/opt/tomcat9/webapps"
          sh "ssh ec2-user@172.31.12.240 /opt/tomcat9/bin/shutdown.sh "
          sh "ssh ec2-user@172.31.12.240 /opt/tomcat9/bin/startup.sh "
         }
      }
    }
 }
}

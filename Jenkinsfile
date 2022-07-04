pipeline {
  agent any
    stages{
      stage("SCM Checkout"){
      steps{
        git credentialsId: 'ramsrimathi', url: 'https://github.com/ramsrimathi/my-ap',branch: "master"
        }
    }
    stage("maven Build"){
      steps{
        sh "mvn clean package"
      }
    }
  }
}

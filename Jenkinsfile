pipeline{
  agent anay 
  tools {
  maven 'maven2'
}
  stages{
    stage{
      steps("git  Checkout"){
        git credentialsId: 'ramsrimathi', url: 'https://github.com/ramsrimathi/my-ap',Branch "master"
      }
    }
     stage{
       steps("maven Build"){
        sh "mvn clean package" 
       }
    }
  }

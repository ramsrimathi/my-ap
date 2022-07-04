pipline {
  agent any
    stages{
      stage("SCM checkout"){
      steps{
        git credentialsId: 'ramsrimathi', url: 'https://github.com/ramsrimathi/my-ap'
        }
    }
    stage("maven build"){
      steps{
        sh "mvn clean package"
      }
    }
  }
}

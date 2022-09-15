pipeline{
  agent any
  stages{
    stage("verify tooling"){
      steps{
      sh """
        docker version
        docker info
        docker conmpose version
        curl --version
        jq --version
       """
      }
    }
  }
}

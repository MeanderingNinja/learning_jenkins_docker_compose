// Intially this works. However today20220929, it gives me address 3001 already in use error. 
pipeline{
  agent any
  stages{
    stage("verify tooling"){
      steps{
      sh """
        docker version
        docker info
        docker compose version
        curl --version 
        echo pwd
       """
      }
    }
    stage("Prune Docker data"){
      steps{
        sh "docker system prune -a --volumes -f"
      }
    }
    
    stage("Start Container"){
      steps{
        sh "docker compose up -d --no-color --wait"
        sh "docker compose ps"
      }
    }
    stage("Run tests against the container"){
      steps {
        sh "curl http://localhost:3001/param?query=demo"
      }
    }
  }
  post {
    always {
      sh "docker compose down --remove-orphans -v"
      sh "docker compose ps"
    }
  }
}
//https://www.youtube.com/watch?time_continue=168&v=ZPD_PzGOvFM&feature=emb_logo

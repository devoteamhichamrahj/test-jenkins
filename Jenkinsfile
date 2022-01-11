pipeline {
  environment {
    registry = "devohichamrahj/test"
    registryCredential = 'dockerhub'
    dockerImage = 'test'
  }
  agent any
    
    
  stages {
        
    stage('printing output') {
      steps{
        sh "echo 'testing jenkins'" 
      }
    }
  }
}

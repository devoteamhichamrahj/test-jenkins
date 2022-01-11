pipeline {
  environment {
    registry = "devohichamrahj"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/devoteamhichamrahj/test-jenkins'
      }
    }
    stage('Remove Unused docker image') {
      steps{
        echo "testing jenkins" 
      }
    }      
  }
}

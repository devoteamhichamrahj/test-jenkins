pipeline {
  environment {
    registry = "devohichamrahj/test"
    registryCredential = 'dockerhub'
    dockerImage = 'test'
  }
  agent any
    
    
  stages {
        
    stage('Cloning Git') {
      steps {
        script {
         git clone 'https://github.com/devoteamhichamrahj/test-jenkins'
      
        }
      }
    }
    stage('printing output') {
      steps{
        echo "testing jenkins" 
      }
    }
    
    stage('remove image'){
      steps{
       sh "docker rmi devohichamrahj/test" 
      }
    }
    
    stage('build image') {
      steps{
        script{
          docker.withRegistry('', registryCredential)
          dockerImage.push()
        }
      }
    }
  }
}

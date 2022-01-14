pipeline {
  environment {
    registry = "devohichamrahj/repo"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    
  tools {nodejs "node js"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ousshsn/authapp'
      }
    }
        
    stage('Install dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Install dotenv') {
      steps {
        bat 'npm install'
      }
    }
     
    stage('Test') {
      steps {
        bat 'npm i -g mocha && npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }      
  }
}
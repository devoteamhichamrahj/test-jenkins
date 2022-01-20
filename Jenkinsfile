pipeline {
  environment {
    registry = "devohichamrahj/docker-test"
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
        bat 'npm install -g win-node-env'
      }
    }
    stage('Test') {
      steps {
        bat 'npm test'
      }
    }
    stage('Building image') {
      steps{
          bat "docker build -t %registry%:%BUILD_NUMBER% ."
      }
    }
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            bat "docker push %registry%:%BUIlD_NUMBER%"
          }
        }
      }
    }
    stage('deploy with ansible on kubernetes') {
      steps{
        sh "ansible-playbook  ./k8s-files/ansible-deploy.yaml --extra-vars \"image_id=${image_id}\""
      }
    }    
  }
}
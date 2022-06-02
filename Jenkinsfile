pipeline {
    agent any
    
    environment {
    registry = '259289693704.dkr.ecr.us-east-1.amazonaws.com/devops_repository'
    registryCredential = 'jenkins-ecr'
    dockerimage = ''
  }
    stages {
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/dodzi2022/Aws-Eks.git'
            }
        }
        stage('Build Image') {
            steps {
                script{
                   
                    sh 'docker build -t webapp:$BUILD_NUMBER .'
                } 
            }
        }
        stage('Deploy image') {
            steps{
                script{ 
                    docker.withRegistry("https://"+registry,"ecr:us-east-1:"+registryCredential) {
                        dockerImage.push()
                    }
                }
            }
     }
   }      
 } 

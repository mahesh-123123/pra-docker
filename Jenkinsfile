pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/mahesh-123123/pra-docker.git'
            }
        }
        stage('Maven Build') {
            steps {
                bat 'mvn clean'
                bat 'mvn install'
                bat 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                  bat 'docker build -t maheshreddy123/tom:v1 .'
                 
                }
            }
        }
        
          stage('Deploy Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub',  url: '') {
                bat 'docker push maheshreddy123/tom:v1'
               
                }
              }
            }
          }
        
        
    }
}

pipeline {
    agent any
 
  
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/rupar19/project.git'
             
          }
        }
  stage('Build') {
           steps {
             
                sh 'mvn package'             
          }
        }
     stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t calc:latest .' 
                sh 'docker tag calcapp rupar19/calc:latest'
                //sh 'docker tag scalcapp rupar19/calcapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub_id", url: "" ]) {
          sh  'docker push rupar19/calc:latest'
        //  sh  'docker push rupar19/calc:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
          steps {
               
       sh "docker run -dt -p 5002:8080 rupar19/calc"
 
            }
        }
     stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.88.242 run -dt -p 5002:8080 rupar19/calc"
 
            }
        }
     
    }
 }

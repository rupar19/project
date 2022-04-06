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
              
                sh 'docker build -t calcapp:latest .' 
                sh 'docker tag calcapp rupar19/calcapp:latest'
                //sh 'docker tag scalcapp rupar19/calcapp:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub_id", url: "" ]) {
          sh  'docker push rupar19/calcapp:latest'
        //  sh  'docker push rupar19/calcapp:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
   {
               // sh "docker run -d -p 8003:8080 rupar19/calcapp"
       sh "docker run -dt -p 9090:8080 rupar19/calcapp"
 
            }
        }
     

    }
 }

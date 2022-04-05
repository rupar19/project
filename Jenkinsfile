pipeline {
    agent any

    stages {
        
        stage('Validate') {
            steps {
                sh 'mvn validate'
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
    
        stage('Deploy') {
            steps {
              sshagent(['deploy-artifact']) {
                  
                     sh 'scp -o StrictHostKeyChecking=no target/WebAppCal-1.3.5.war centos@172.31.88.242:~/apache-tomcat-7.0.94/webapps/'
              
                    }
            }
        }

    }
}

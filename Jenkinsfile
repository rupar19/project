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
 
                  {
                      scp target/WebAppCal-1.3.5.war centos@44.203.60.229:~/apache-tomcat-7.0.94/webapps
              
              
                  }
              }            

}
        }

    }
}

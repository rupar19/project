pipeline {
    agent { docker { image 'maven:3.3.3' } }
     tools {maven "MyMaven '} 
      stages {
        stage('log version info') {
      steps {
     git 'https://github.com/rupar19/project.git'
        sh 'mvn --version'
        sh 'mvn clean install'
      }
    }
  }
}

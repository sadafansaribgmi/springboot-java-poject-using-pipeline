pipeline {   
    agent any 
    tools{
        jdk 'jdk-8'
        maven 'maven3'
    }

    stages {
        stage('Git checkout') {
            steps {
             git changelog: false, url: 'https://github.com/sadafansaribgmi/springboot-java-poject-using-pipeline.git'     
            }
        }
        
        stage('maven build') {
            steps {
                sh "mvn clean install"
                 }
        }
         stage('Deploy') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'tomcatserver1', path: '', url: 'http://13.233.138.186:8080')], contextPath: '/app', war: '**/*.war'

           }
        }
     
  }
}

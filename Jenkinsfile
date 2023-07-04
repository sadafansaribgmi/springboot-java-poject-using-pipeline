pipeline {   
    agent any 
    tools{
        jdk 'jdk-8'
        maven 'maven3'
    }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/sadafansaribgmi/springboot-java-poject-using-pipeline.git'            }
        }
        
        stage('maven build') {
            steps {
                sh "mvn clean install"
                 }
        }
        
        stage('docker build and push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'Docker crendcial') {
                     sh 'docker build -t sadaf46/jawa-web .'
                     sh 'docker push sadaf46/jawa-web   '
    } 
}
                 }
        }
        
        
         
    }
}

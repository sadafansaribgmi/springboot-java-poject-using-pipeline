pipeline{
    agent any
    tools{
      maven 'maven'
    }  
    stages{
        stage("pulling from scm"){
            steps{
                git 'https://github.com/sadafansaribgmi/springboot-java-poject-using-pipeline.git'
            }
    
          post{
           always{
            echo "========always========"
            }
            success{
             echo "========pipeline executed successfully ========"
            }
           failure{
            echo "========pipeline execution failed========"
            }
          }
        }
        stage("test"){
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    echo "========A test executed successfully========"
                }
                failure{
                    echo "========A test execution failed========"
                }
            }
        }
        stage("Build"){
            steps{
                sh 'mvn package'
            }
            post{
                success{
                    echo "========A package executed successfully========"
                }
                failure{
                    echo "========A package execution failed========"
                }
            }
        }
        stage("Deploy on production"){
            steps{
               deploy adapters: [tomcat9(credentialsId: 'tomcatserver1', path: '', url: 'http://13.233.138.186:8080')], contextPath: '/app', war: '**/*.war'
             }
             post{
                success{
                    echo "========A Deploy executed successfully========"
                }
                failure{
                    echo "========A Deploy execution failed========"
                }
            }
        }
            
      }
    }

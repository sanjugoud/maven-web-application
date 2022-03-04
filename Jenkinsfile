pipeline {
    agent any 
    tools{
        maven 'maven3'
    }
    stages{
        stage('git checkout ')
        {
            steps{
                git 'https://github.com/sanjugoud/maven-web-application.git'

            }
        }
        stage('static-code analysis '){
            steps{
             sh 'mvn sonar:sonar'
    
            }
        }
        stage('build package '){
            steps{
             sh 'mvn clean package'
    
            }
        }
        stage('publish to nexus'){
            steps{
             sh 'mvn deploy'
    
            }
        }
         stage('deploy to tomcat'){
            steps{
             sshagent(['ttomcat_pem']) {
                  sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.233.151.128:/opt/tomcat9/webapps/'
    
             }
    
            }
        }

    }
}

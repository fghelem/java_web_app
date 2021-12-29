pipeline {
    agent any
    tools {
          maven 'maven 3.6.0'
          jdk 'JAVA_HOME'
          }
     

    stages {
        stage("get source code") {

             steps  {
                  checkout scm
             }   
        }
        stage("Clean") {
            steps {
                sh "mvn -version"
                sh "mvn clean"
            }
        }

        stage("jococo") {
            steps {
            script {
            jacoco()
           
            }
            }
        }
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn  package"
            }
        }

        stage("test") {
            steps {
                 
                sh "mvn test"
            }
        }

        
    }

    post {
        always {
            cleanWs()
        }
    }
}
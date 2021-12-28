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
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean compile"
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
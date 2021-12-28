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
            
           jacoco execPattern: '**/**', maximumBranchCoverage: '50', maximumClassCoverage: '80', maximumComplexityCoverage: '50', maximumLineCoverage: '80', maximumMethodCoverage: '80', minimumBranchCoverage: '50', minimumComplexityCoverage: '50', sourceInclusionPattern: '**/*.java'
          
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
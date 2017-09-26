pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Server') {
          agent {
            docker {
              image 'maven/3.5-jdk-8-slim'
            }
            
          }
          steps {
            sh 'echo "Building the server code..."'
          }
        }
        stage('Client') {
          steps {
            sh 'echo "Building the client code..."'
          }
        }
      }
    }
    stage('Test') {
      parallel {
        stage('Chrome') {
          agent {
            docker {
              image 'selenium/standalone-chrome'
            }
            
          }
          steps {
            sh 'mvn test -Dbrowser=chrome'
          }
        }
        stage('Firefox') {
          agent {
            docker {
              image 'selenium/standalone-firefox'
            }
            
          }
          steps {
            sh 'mvn test -Dbrowser=firefox'
          }
        }
      }
    }
    stage('QA') {
      agent {
        docker {
          image 'tomcat/8.0-jre-8'
        }
        
      }
      steps {
        sh 'sh \'tomcat/run.sh\''
      }
    }
  }
}
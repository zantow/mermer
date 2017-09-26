pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Server') {
          agent {
            docker {
              image 'maven:3.5-jdk-8-slim'
            }
            
          }
          steps {
            sh 'echo "Building the server code..."'
            stash(name: 'server', includes: '**/*.war')
          }
        }
        stage('Client') {
          steps {
            sh 'echo "Building the client code..."'
            stash(name: 'client', includes: '**/dist/*.js')
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
        sh '''APP_DIR=/var/lib/tomcat6/webapps
# get rid of old war file
rm -rf $APP_DIR/ROOT
# copy new war file
cp example_dir/ROOT.war $APP_DIR
# restart tomcat
service tomcat6 restart'''
        input(message: 'Deploy!', ok: 'Go, go, go!')
      }
    }
    stage('Deploy') {
      steps {
        unstash 'server'
        unstash 'client'
        echo 'sh "scp *.war production/"'
      }
    }
  }
}
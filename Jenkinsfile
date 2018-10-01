pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''echo 'some report' > target/report.html'''
        publishHTML (target: [
          allowMissing: false,
          alwaysLinkToLastBuild: false,
          keepAll: true,
          reportDir: 'target',
          reportFiles: 'report.html',
          reportName: "RCov Report"
        ])
      }
    }
  }
}

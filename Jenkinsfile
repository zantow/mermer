pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''mkdir -p target
        echo 'some report' > target/report.html
        echo 'some report2' > target/report _2.html
'''
        publishHTML (target: [
          allowMissing: false,
          alwaysLinkToLastBuild: false,
          keepAll: true,
          reportDir: 'target',
          reportFiles: '*.html',
          reportName: "Some_RCov Report"
        ])
      }
    }
  }
}

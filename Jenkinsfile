pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        withSonarQubeEnv installationName="uhhh-the-installationName" {
                    echo 'SonarQube'
                  }
          withSonarQubeEnv('maybe-the-installationName') {
            echo 'SonarQube'
          }

          sh '''#test
for e in 1 2 3 4 5 6 7 8 9 0; do
echo "step $e happening"
sleep 1
echo "more stuff happening - $e"
sleep 1
echo "still more stuff happening - $e"
sleep 1
echo "finished $e"
sleep 1
done
'''
        }
      }
      stage('Test') {
        parallel {
          stage('Chrome') {
            steps {
              sh '''for e in 1 2 3 4 5 6 7 8 9 0; do
echo "chrome $e happening"
sleep 1
echo "more stuff happening - $e"
sleep 1
echo "still more stuff happening - $e"
sleep 1
echo "finished $e"
sleep 1
done
'''
            }
          }
          stage('Firefox') {
            steps {
              sh '''for e in 1 2 3 4 5 6 7 8 9 0; do
echo "firefox $e happening"
sleep 1
echo "more stuff happening - $e"
sleep 1
echo "still more stuff happening - $e"
sleep 1
echo "finished $e"
sleep 1
done
'''
            }
          }
          stage('IE') {
            steps {
              retry(count: 5) {
                sh '''for e in 1 2 3 4 5 6 7 8 9 0; do
echo "ie $e happening"
sleep 1
echo "more stuff happening - $e"
sleep 1
echo "still more stuff happening - $e"
sleep 1
echo "finished $e"
sleep 1
done
'''
              }

            }
          }
        }
      }
      stage('Deploy') {
        steps {
          sh '''for e in 1 2 3 4 5 6 7 8 9 0; do
echo "deploy $e happening"
sleep 1
echo "more stuff happening - $e"
sleep 1
echo "still more stuff happening - $e"
sleep 1
echo "finished $e"
sleep 1
done
echo done'''
        }
      }
    }
  }

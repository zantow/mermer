pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''for e in a b c d e f g h i j k l m n o p q r s t u v w x y z 1 2 3 4 5 6 7 8 9 0; do
echo "step happening"
echo $e
sleep 2
done
'''
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Chrome": {
            sh '''for e in asdf fwef oijewf lwejf lwekfj wlekfjwlekfj wef lwekfj welkf jwlefkj wlefj; do
echo $e
sleep 1
done
'''
            
          },
          "Firefox": {
            sh '''for e in asdf fwef oijewf lwejf lwekfj wlekfjwlekfj wef lwekfj welkf jwlefkj wlefj; do
echo $e
sleep 3
done
'''
            
          },
          "IE": {
            retry(count: 5) {
              sh '''for e in asdf fwef oijewf lwejf lwekfj wlekfjwlekfj wef lwekfj welkf jwlefkj wlefj; do
echo $e
sleep 2
done
'''
            }
            
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        sh '''for e in asdf fwef oijewf lwejf lwekfj wlekfjwlekfj wef lwekfj welkf jwlefkj wlefj; do
echo $e
sleep 1
done
'''
      }
    }
  }
}

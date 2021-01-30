pipeline {
  agent any

  environment {
    DEMO = '1.3'
  }

  stages {
    stage('Stage 1') {
      steps {
        echo "This is my build number $BUILD_NUMBER and the $DEMO "
        sh '''
        echo "using the multiline code"
        chmod +x test.sh
        ./test.sh
        '''

      }
    }

  }
  environment {
    demo = '1'
  }
}

pipeline {
  agent any
  stages {
    stage('Stage 1') {
      steps {
        echo 'This is my build number $BUILD_NUMBER'
        sh 'echo "This is by build number $BUILD_NUMBER of demo $DEMO "'
        sh 'echo "This is second build $DEMO" '
      }
    }

  }
  environment {
    demo = '1'
  }
}

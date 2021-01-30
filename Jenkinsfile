pipeline {
  agent any

 environment
    {
        DEMO = '1.3'
        RELEASE = '20.4'
    }

  stages
  {
    stage('Build')
    {
      agent any
      environment
      {
         LOG_LEVEL = 'INFO'
       }

      steps
      {
        echo "This is my build number $BUILD_NUMBER and the $DEMO "
        sh '''
        echo "using the multiline code"
        chmod +x test.sh
        ./test.sh
        '''
      }
    }
    stage('Test')
        {
          agent any
          steps
          {
            echo "This is my Test number $BUILD_NUMBER and the $DEMO "
          }
        }
}

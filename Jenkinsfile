pipeline {
    agent any

    environment 
    {
        DEMO = "1.3"
        RELEASE = "20.4"
    }

    stages 
    {
        stage("Build")
        {
            environment 
            {
                LOG_LEVEL = "INFO"
            }

            steps {
                echo "Building release ${RELEASE} with log level ${LOG_LEVEL}"
                sh ' chmod +x test.sh'
                withCredentials([string(credentialsId: 'SlackToken' , variable: 'SlackToken')]) {
                sh '''
                    ./test.sh
                    '''
                }
            }
        }
        stage('Test')
        {
            steps
            {
                echo "Testing Release ${RELEASE}"
                script
                {
                    if (Math.random() > 0.5)
                    {
                      throw new Exception()
                    }
                }
              writeFile file: 'test-results.txt', text:'passed'
            }
         }
      }
       post {
               success {
                   archiveArtifacts 'test-results.txt'
                    slackSend(
                       channel: "#Builds",
                       color:   "good",
                       message: "build status success -  ${env.BUILD_NUMBER} ")
               }
               failure {
                    slackSend(
                       channel: "#Builds",
                       color: "danger",
                        message: "build status failure -  ${env.BUILD_NUMBER} ")
                }
           }
}
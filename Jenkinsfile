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
                echo "This is my Test number $BUILD_NUMBER and the $DEMO and $RELEASE "
                writeFile file: 'test-results.txt', text:'passed'
             }
        }
        stage('Send Notification') {
                    steps {
                        script {
                            def color = "${params.MESSAGE_STATUS}" == "GOOD"? "good" : "warning"
                            slackSend(color: "${color}", message: "${params.MESSAGE}", channel: "${params.CHANNEL}")
                        }
                    }
                }
    }
}
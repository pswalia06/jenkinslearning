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

            parallel {
                stage("linux-arm64"){
                    steps {
                        echo "Building release ${RELEASE} for ${LOG_LEVEL} with ${STAGE_NAME}"
                    }
                }

                stage("linux-amd64"){
                    steps {
                        echo "Building release ${RELEASE} for ${LOG_LEVEL} with ${STAGE_NAME}"
                    }
                }

                stage("Window-amd64"){
                    steps {
                        echo "Building release ${RELEASE} for ${LOG_LEVEL} with ${STAGE_NAME}"
                    }
                }
            }
        }

        stage("Test")
        {
            steps 
            {
                echo "This is my Test number $BUILD_NUMBER and the $DEMO and $RELEASE "
                writeFile file:test-results.txt, text:passed
            }
        }
    }

    post {
        success {
            archiveArtifacts "test-results.txt"
        }
    }
}
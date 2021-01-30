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
                echo "This is my Test number $BUILD_NUMBER and the $DEMO and $RELEASE  "
            }
        }

        stage("Deploy"){
            input {
                message "Deploy?"
                ok "Do it !"
                parameters {
                    string(name:"TARGET_ENVIRONMENT", defaultValue:"PROD", description:"Target Deployment Environment")
                }
            }

            steps {
                echo "This is my Test number $BUILD_NUMBER and the $DEMO and $TARGET_ENVIRONMENT "
            }
        }
    }

    post {
        always {
            echo "print weather deploy or not"
        }
    }
}
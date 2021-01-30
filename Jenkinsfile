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
            agent any
            environment 
            {
                LOG_LEVEL = "INFO"
            }

            steps 
            {
                echo "This is my build number $BUILD_NUMBER and the $DEMO and $LOG_LEVEL "
            }
        }

        stage("Test")
        {
            agent any
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

                steps {
                    echo "This is my Test number $BUILD_NUMBER and the $DEMO and $RTARGET_ENVIRONMENT"
                }
            }
        }
    }

    post {
        always {
            echo "print wheatehr deploy or not"
        }
    }
}
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
                echo "This is my build number $BUILD_NUMBER and the $DEMO "
                sh "\n        echo "using the multiline code"\n        chmod +x test.sh\n        ./test.sh\n        "
            }
        }

        stage("Test")
        {
            agent any
            steps 
            {
                echo "This is my Test number $BUILD_NUMBER and the $DEMO "
            }
        }
    }
}
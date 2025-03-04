pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/path/to/source/code"
        TESTING_ENVIRONMENT = "Netlify"
        PRODUCTION_ENVIRONMENT = "AkshitGoyal"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from ${DIRECTORY_PATH}"
                echo "Compile the code and generate any necessary artifacts"
            }
        }

        stage('Test') {
            steps {
                echo "Run unit tests"
                echo "Run integration tests"
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Check the quality of the code"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy the application to ${TESTING_ENVIRONMENT}"
            }
        }

        stage('Approval') {
            steps {
                echo "Waiting for approval..."
                sleep(time: 10, unit: 'SECONDS')
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the application to ${PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}

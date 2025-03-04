pipeline {
    agent {
        docker {
            image 'node:18'  // Use Node.js 18 Docker image
        }
    }

    environment {
        DIRECTORY_PATH = "/path/to/source/code"
        TESTING_ENVIRONMENT = "TestEnv"
        PRODUCTION_ENVIRONMENT = "AkshitGoyal"
        NETLIFY_AUTH_TOKEN = credentials('netlify_token')
        NETLIFY_SITE_ID = "201a01bb-3bc6-4fac-a5ad-b9f45c416bc9"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo/react-project.git'  // Replace with your GitHub repo
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing project dependencies..."
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                echo "Building the React app..."
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo "Running unit tests..."
                sh 'npm test'
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Checking the quality of the code..."
            }
        }

        stage('Deploy to Netlify') {
            steps {
                echo "Deploying to Netlify..."
                sh 'npm install -g netlify-cli'  // Ensure Netlify CLI is installed
                sh 'netlify deploy --prod --dir=build --auth=$NETLIFY_AUTH_TOKEN --site=$NETLIFY_SITE_ID'
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
                echo "Deploying the application to ${PRODUCTION_ENVIRONMENT}"
            }
        }
    }
}

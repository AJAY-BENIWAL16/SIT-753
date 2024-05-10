pipeline {
    agent any
    
    environment {
        CODE_DIRECTORY = "/direct/codefolder/access/"
        TESTING_ENV = "testing_my_environment"
        PROD_ENV = "New_Prod_Environment"
    }
    
    stages {
        stage('Fetching Source Code') {
            steps {
                echo "Fetching source code from: ${env.CODE_DIRECTORY}"
                echo "Compiling the code and creating artifacts"
            }
        }
        
        stage('Automated Testing') {
            steps {
                echo "Executing automated unit tests"
                echo "Running integration tests"
            }
        }
        
        stage('Code Analysis and Quality Check') {
            steps {
                echo "Performing code quality analysis"
            }
        }
        
        stage('Deploy to Testing Environment') {
            steps {
                echo "Deploying the application to ${env.TESTING_ENV}"
            }
        }
        
        stage('Manual Approval') {
            steps {
                echo "Waiting for manual approval..."
                sleep(time: 15, unit: 'SECONDS')
            }
        }
        
        stage('Deploy to Production Environment') {
            steps {
                echo "Deploying the code to ${env.PROD_ENV}"
            }
        }
    }
    
    
    post {
        success {
            mail to: "ajay161098@gmail.com",
            subject: "Build Status Email",
            body: "Build successful."
        }
    }
}

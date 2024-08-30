pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path specified by the environment variable $DIRECTORY_PATH"
                echo "Compile the code and generate any necessary artifacts"
                echo "Using Maven to build automation"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
                echo "Using Maven for testing"
            }
        }
        post{
                success{
                    mail to: "yizhouh8@gmail.com",
                    subject: "Build Status Email",
                    body: "Test success"
                }
                failure {
                    mail to: 'yizhouh8@gmail.com',
                    subject: "Build Status Email",
                    body: "Test Failed"
                }
            }
        stage('Code Analysis') {
            steps {
                echo "Using the SonarQube plugins to analysing the code"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Using the SonarQube plugins to scan the security of code"
            }
            post{
            success{
                mail to: "yizhouh8@gmail.com",
                subject: "Security Scan Result",
                body: "Code Secure"
            }
            failure {
                mail to: 'yizhouh8@gmail.com',
                subject: "Security Scan Result",
                body: "Code Insecure"
            }
        }
        }
        stage('Deploy') {
            steps {
                echo "Deploy the application to the testing environment specified by the environment variable $TESTING_ENVIRONMENT"
                echo "Deploy the application to the AWS server"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "run integration tests on the staging environment to ensure the application functions as expected in a production-like environment. "
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the production environment using the environment variable: $PRODUCTION_ENVIRONMENT"
            }
        }
        
    }
}

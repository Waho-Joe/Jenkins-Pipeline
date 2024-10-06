pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Using Maven to build automation"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
                echo "Using Maven for testing"
            }
            post{
                success{
                    mail to: "yizhouh8@gmail.com",
                    subject: "Test Status Email",
                    body: "Test success"
                }
                failure {
                    mail to: 'yizhouh8@gmail.com',
                    subject: "Test Status Email",
                    body: "Test Failed"
                }
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
                    archiveArtifacts artifacts: 'target.log'
                    emailext(
                        to: "yizhouh8@gmail.com",
                        subject: "Security Scan Result - SUCCESS",
                        body: "The security scan was successful. The code is secure."
                    )
                }
                failure {
                    archiveArtifacts artifacts: 'target.log'
                    emailext(
                        to: 'yizhouh8@gmail.com',
                        subject: "Security Scan Result",
                        body: "Code Insecure"
                    )
                }
            }
        }
        stage('Deploy') {
            steps {
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
                echo "Deploy the code to the AWS server"
            }
        }
        
    }
}

pipeline {
    agent any 
    environment {
        DIRECTORY_PATH = "http://localhost:8080/job/Continuous%20Delivery/"
        TESTING_ENVIRONMENT = "Windows"
        PRODUCTION_ENVIRONMENT = "Joshua"
    }
    stages {
        stage('Build') { 
            steps {
                echo "Building code package using Maven"
            }
        }
        stage('Test') { 
            steps {
                echo "Running unit test and integration tests using Harness tool" 
            }
            post{
                always{
                    mail to: "s222262122@deakin.edu.au"
                    subject: "Test Complete"
                    body: "Logs attached above"
                }
            }
        }
        stage('Code Analysis'){
            steps {
                echo "Checking the quality of code using analysis to industry standard using Harness tool"
            }
        }
        stage('Security Scan'){
            steps{
                echo "Using Snyk tool to check for vulnerabilities in code "
            }
            post{
                always{
                    mail to: "s222262122@deakin.edu.au"
                    subject: "Scan Complete"
                    body: "Logs attached above"
                }
            }
        }
        stage('Deploy to Staging'){
            steps{
                echo "Deploying application to AWS EC2 staging server"
            }
        }
        stage('Integration Tests on Staging'){
            steps{
                echo "Run multple integration tests on staging server mimicing production environment"
            }
        }
        stage('Deploy to Production') { 
            steps {
                echo "Code deployed to AWS EC2 environment"
            }
        }
    }
}
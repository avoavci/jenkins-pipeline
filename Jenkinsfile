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
                success{
                    emailext attachLog: true, body: 'Logs attached above', subject: 'Test Success', to: 'wallplanner7@gmail.com'
                }
                failure{
                    emailext attachLog: true, body: 'Logs attached above', subject: 'Test Failure', to: 'wallplanner7@gmail.com'
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
                success{
                    emailext attachLog: true, body: 'Logs attached above', subject: 'Scan Success', to: 'wallplanner7@gmail.com'
                }
                failure{
                    emailext attachLog: true, body: 'Logs attached above', subject: 'Scan Failure', to: 'wallplanner7@gmail.com'
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

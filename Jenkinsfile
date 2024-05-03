pipeline {
    agent any

    environment {
        // Define environment variables
        APP_NAME = 'MyApp'
        STAGING_SERVER = 'staging.example.com'
        PRODUCTION_SERVER = 'production.example.com'
        EMAIL_RECIPIENT = 's223844277@deakin.edu.au'
    }

    stages {
        stage('Build') {
            steps {
                echo "Building ${env.APP_NAME} using Maven..."
            // Build commands using the environment variable
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests for ${env.APP_NAME}..."
                echo "Running integration tests for ${env.APP_NAME}..."
            // Test commands using the environment variable
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Running code analysis for ${env.APP_NAME} using SonarQube..."
            // Code analysis commands using the environment variable
            }
        }
        stage('Security Scan') {
            steps {
                // Perform the security scan
                sh 'security_scan_command' // Replace with the actual command for the security scan

                // Send email notification for security scan failure
                emailext(
              subject: "Security Scan Failed - ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
              body: "The security scan for ${env.JOB_NAME} is successful. Please take necessary action.",
              to: 's223844277@deakin.edu.au',
              attachLog: true
            )
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying ${env.APP_NAME} to an AWS EC2 instance server: ${env.STAGING_SERVER}..."
            // Deployment commands using the environment variables
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on ${env.STAGING_SERVER}..."
                echo "Running end-to-end tests on ${env.STAGING_SERVER}..."

                emailext(
                    body: 'Tests executed successfully.',
                    subject: 'Pipeline Success',
                    to: 's223844277@deakin.edu.au'
                )
            // Integration test commands using the environment variable
            }
        }
    stage('Deploy to Production') {
        steps {
            echo "Deploying ${env.APP_NAME} to AWS EC2 instance server: ${env.PRODUCTION_SERVER}..."
        // Deployment commands using the environment variables
        }
    }
}


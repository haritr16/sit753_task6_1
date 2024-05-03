pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit tests using junit'
                echo 'Run unit tests using Mocha'
                echo 'Running integration tests using selenium'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code using SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging environment'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
            }
            
            post {
        success {
            mail to: "hariau98@gmail.com",
            subject: "Testing stage",
            body: "Jenkins testing has completed successfully."
        }
        failure {
            mail to: "hariau98@gmail.com",
            subject: "Testing stage",
            body: "Testing failed on staging"
           
        }
    }
    
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production environment...'
            }
             post {
        success {
            mail to: "hariau98@gmail.com",
            subject: "Pipeline Successful",
            body: "Successfully deployed to production."
           
        }
        failure {
            mail to: "hariau98@gmail.com",
            subject: "Pipeline Unsuccessful",
            body: "Deloyment failed"
           
        }
    }
        }
    }
   
}

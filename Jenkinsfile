pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven - A build automation tool.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit tests using junit to test the code'
                echo 'Run unit tests using Mocha'
                echo 'Running integration tests using selenium'
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
        stage('Code Analysis') {
            steps {
                echo 'Analyze the code using code analysis tool - SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP and Dynatrace'
                }
             post {
                success {
                mail to: "hariau98@gmail.com",
                subject: "Security scan Successful",
                body: "Successfully completed security scan"
           
            }
                failure {
                mail to: "hariau98@gmail.com",
                subject: "Security scan Unsuccessful",
                body: "Security scan failed!!"
           
            }
            }
            
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging environment AWS EC2 instance'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Performing integration tests on staging environment using citrus tool'
            }
            
            
    
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production environment-AWS EC2 instance'
            }

        }
        }

    post {
        always {
            script {
                def consoleLogUrl = "${env.BUILD_URL}/consoleText"
                emailext subject: currentBuild.result == 'SUCCESS' ? "Pipeline Successful" : "Pipeline Failed",
                          body: currentBuild.result == 'SUCCESS' ? "Your Jenkins pipeline has completed successfully.\nConsole Log: ${consoleLogUrl}" : "Your Jenkins pipeline has failed.\nConsole Log: ${consoleLogUrl}",
                          to: "hariau98@gmail.com"
            }
            
        }
    }
        
    
   
}

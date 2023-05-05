pipeline {
    agent any

    environment {
        TESTING_ENVIRONMENT = "test-env"
        PRODUCTION_ENVIRONMENT = "prod-env"
    }

    stages {
        stage('Build') {
            steps {
                // sh 'mvn clean package'
                echo "Fetching source code from github web hook"
                echo "Compiling the code and generating artifacts"
            }
        }
        stage('Unit Tests') {
            steps {
                // sh 'mvn test'
                // run unit tests with Selenium or TestNG
                echo "Running unit tests"
            }
        }
        stage('Code Analysis') {
            steps {
                // withSonarQubeEnv('SonarQube') {
                //     sh 'mvn sonar:sonar'
                // }
                echo "Checking the quality of the code"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Running security scan"
                //sh 'security_scan.sh -cmd -outfile report.html'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // use AWS CLI or similar to deploy to staging server
                echo "Deploying the application to testing environment: ${env.TESTING_ENVIRONMENT}"
                
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // run integration tests on staging environment
                echo "Running integration tests"
            }
        }
        stage('Deploy to Production') {
            steps {
                // use AWS CLI or similar to deploy to production server
                echo "Deploying the code to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }

    post {
        always {
            emailext to: "yasey.omal@gmail.com",
            subject: "jenkins build:${currentBuild.currentResult}: ${env.JOB_NAME}",
            body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}<br>More Info can be found here: ${env.BUILD_URL}",
            attachLog: true
        }
    }
}

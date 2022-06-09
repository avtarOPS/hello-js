pipeline {
    agent any
    
    environment {
        AWS_DEFAULT_REGION = "us-west-2"
    }
    
    stages {
        stage("Code Checkout") {
        steps {
        git branch: 'main',
            url: 'https://github.com/avtarOPS/hello-js.git'
        }
 }        
        stage('Sonarqube') {
            steps {
                script{
                    def scannerHome = tool 'sonarqube';
                }
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
}
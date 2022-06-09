pipeline {
    agent any
    
    environment {
        AWS_DEFAULT_REGION = "us-west-2"
    }
    
    stages {      
        stage('Sonarqube') {
            steps {x
                script{
                scannerHome = tool 'Sonar';
                }
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=$BUILD_NUMBER"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
}
}
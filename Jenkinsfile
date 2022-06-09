pipeline {
    agent any
    
    environment {
        AWS_DEFAULT_REGION = "us-west-2"
    }
    
    stages {      
        stage('Sonarqube') {
            steps {
                   def scannerHome = tool name: 'sonar_scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
}
}
pipeline {
    agent any
    
    environment {
        AWS_DEFAULT_REGION = "us-west-2"
    }
    
    stages {      
        stage('Sonarqube') {
            steps {
                script{
                scannerHome = tool 'Sonar';
                }
                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectVersion=$BUILD_NUMBER"
                }
            }
        }
}
}
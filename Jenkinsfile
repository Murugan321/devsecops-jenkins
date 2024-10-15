pipeline {
    agent any
    tools { 
        maven 'Maven_3_5_2'  
    }
    stages {
        stage('CompileandRunSonarAnalysis') {
            steps {	
                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=devsecops3_devsecops -Dsonar.organization=DevSecops3 -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=9707f4930eb6802979b27b3a9b04c4361d74e6f0'
            }
        }

        stage('RunSCAAnalysisUsingSnyk') {
            steps {		
                echo 'Testing...'
                snykSecurity(
                    snykInstallation: 'synktool',
                    snykTokenId: 'synk_token',
                    failOnError: 'false',
                    failOnIssues: 'false'
                )
            }
        }
    }    
}    

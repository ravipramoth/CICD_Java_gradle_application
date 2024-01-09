pipeline {
    agent any 
    environment {
        SCANNER_HOME=tool 'sonar-tool'
        VERSION = "${env.BUILD_ID}"
            }
    stages{
        stage("sonar-scanner") {
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'snoar-token') {
                    // sh 'chmod +x gradlew'
                    // sh './gradlew sonarqube'
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=gradel \
                    -Dsonar.projectKey=gradeel '''

               }
            }
        }
    }
}
}

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
                    
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=gradel -Dsonar.login=admin \
                    -Dsonar.projectKey=gradeel -Dsonar.sources=src/main -Dsonar.password=admin@123 \
                    -Dsonar.test=src/test -Dsonar.java.binaries=build/classes/java  '''

               }
            }
        }
    }
}
}

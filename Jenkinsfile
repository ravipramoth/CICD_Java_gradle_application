pipeline {
    agent any 
    environment {
        SCANNER_HOME = tool 'sonar-tool'
        VERSION = "${env.BUILD_ID}"
    }
    stages {
        stage("sonar-scanner") {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh """
                            ${SCANNER_HOME}/bin/sonar-scanner \
                            -Dsonar.projectName=gradel \
                            -Dsonar.projectKey=gradeel \
                            -Dsonar.login=admin \
                            -Dsonar.password=admin@123 \
                            -Dsonar.sources=src/main \
                            -Dsonar.tests=src/test \
                            -Dsonar.exclusions=**/*.java
                        """
                    }
                }
            }
        }

        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                    script {
                        def qg = waitForQualityGate()
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        }
                    }
                }
            }
        }
    }
}

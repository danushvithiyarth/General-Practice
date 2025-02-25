pipeline {
    agent any
    tools {
        nodejs 'npm-23.8.0'
    }
    environment{
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage("Install Dependency") {
            steps {
                sh 'npm install --no-audit'
            }
        }
        stage("npm test") {
            steps {
                sh 'npm test -- --coverage'
            }
        }
        stage('SonarQube-analysis') { 
            steps {
                script {
                    echo "Sonar scanner"
                    withSonarQubeEnv('sonar-server') {
                    sh '''
                      ${SCANNER_HOME}/bin/sonar-scanner \
                      -Dsonar.projectKey=testkey \
                      -Dsonar.projectName=test-app \
                      -Dsonar.javascript.lcov.reportPaths=./coverage/lcov.info
                     '''
                    }     
                }
           }
        }
    }
}

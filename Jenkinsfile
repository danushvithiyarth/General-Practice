pipeline {
    agent any
    tools {
        nodejs 'npm-23.8.0'
    }

    stages {
        stage("Install Dependency") {
            steps {
                sh 'npm install --no-audit'
            }
        }

        stage("NPM Dependency Check and Fix") {
            steps {
                sh '''
                 npm audit 
                 echo $?
                 npm audit fix --force 
                '''
            }
        }
        stage("NPM Dependency check") {
            steps {
                sh '''
                 npm audit 
                 echo $?
                '''
            }
        }
    }
}

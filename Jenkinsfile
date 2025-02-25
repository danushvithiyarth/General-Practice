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

        stage("NPM Dependency Check") {
            steps {
                sh '''
                 npm audit 
                 echo $?
                '''
            }
        }
        stage("NPM Dependency fix") {
            steps {
                sh '''
                 npm audit fix --force 
                 echo $?
                '''
            }
        }
    }
}

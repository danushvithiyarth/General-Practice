pipeline {
    agent any
    tools {
        nodejs 'npm-23.8.0'
    }
    
    stages {
        stage("Install Dependency") {
            steps {
                dir('coit-frontend/') {
                    sh 'nodejs -v'
                    sh 'npm -v'
                    sh 'npm install --no-audit'
                }
            }
        }
    }
}

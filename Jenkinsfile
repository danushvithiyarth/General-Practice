pipeline {
    agent any
    tools {
        nodejs 'npm-23.8.0'
    }
    
    stages {
        stage("Install Dependency") {
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'npm install --no-audit'
            
            }
        }
    }
}

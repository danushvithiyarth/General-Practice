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

        stage("Dependency Check") {
            steps {
                parallel (
                    "NPM Dependency Check" : {
                        sh '''
                            npm audit --audit-level=high
                            echo $?
                        '''
                    },
                    "OWASP Dependency Check" : {
                        sh '''
                            dependencyCheck --scan ./ \
                                --format ALL \
                                --prettyPrint \
                                --nvdApiKey e3b86212-bcc1-4222-9fe5-77bb48ab44ff
                        '''
                    }
                )
            }
        }
    }
}

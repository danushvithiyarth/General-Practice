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
            parallel {
                stage("NPM Dependency Check") {
                    steps {
                        sh '''
                            npm audit --audit-level=high
                            echo $?
                        '''
                    }
                }

                stage("OWASP Dependency Check") {
                    steps {
                        dependencyCheck additionalArguments: '''
                            --scan ./ \
                            --format ALL \
                            --prettyPrint \
                            --nvdApiKey e3b86212-bcc1-4222-9fe5-77bb48ab44ff
                        ''', odcInstallation: 'OWASP-10.0.0'
                    }
                }
            }
        }
    }
}

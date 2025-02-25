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
                        dependencyCheck additionalArguments: '''--scan ./ \
                            --format ALL \
                            --prettyPrint''', 
                            odcInstallation: 'OWASP-10.0.0'
                    }
                }
            }
        }
    }
}
     
        
        //stage("SonarQube Analysis") {
          //  steps {
            //    withSonarQubeEnv('sonar-server') {
              //      sh '''
                //      ${SCANNER_HOME}/bin/sonar-scanner \
                  //    -Dsonar.projectKey=nodekey \
                    //  -Dsonar.projectName=nodejs \
                      //-Dsonar.sources=. \
                     // -Dsonar.exclusions=**/*.java
                    //'''
        //        }
       //     }
       // }
       // stage("Build Docker Image") {
         //   steps {
          //      script {
          //          sh "docker build -t react-app:v1 -f coit-frontend/Dockerfile-multistage coit-frontend/"
           //         sh "docker images"
            //        sh "docker image prune -f"
            //    }
           // }
       // }
       // stage("Run Docker Container") {
         //   steps {
         //       script {
           //         sh "docker run -d -p 80:80 react-app:v1"
             //       sh "docker ps"
             //   }
           // }
      //  }


        // stage("Deploy"){
        //     steps{
        //         sh "cd coit-frontend && cp build/* /var/www/html/"
        //     }
        // }
        
    
   // post{
        // success{
        //     archiveArtifacts artifacts: '**/build', followSymlinks: false
        // }
        // failure{
        //     emailext body: '''Jenkins has failed to build the Job. Please find the information below.

        //                     Name of the Job: ${JOB_NAME}
        //                     Build that failed: ${BUILD_NUMBER}

        //                     Please check the logs at ${BUILD_URL}


        //                     Thanks
        //                     Jenkins''', subject: 'Failed ${JOB_NAME}', to: 'basil@coit.io'
        // }
   // }


pipeline {
   agent any

    stages {
      stage('Build') {
         steps {
            
           sh "cd complete"

            // Run Maven on a Unix agent.
            sh "mvn clean install"

            // To run Maven on a Windows agent, use
            // bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         
         }
      }
   }


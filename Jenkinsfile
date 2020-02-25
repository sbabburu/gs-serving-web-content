pipeline {
   agent any

    stages {
      stage('Build') {
         steps {
            
           
            // Run Maven on a Unix agent.
            sh " cd /var/lib/jenkins/workspace/java-k8s/complete/"
            sh "mvn clean install"

            // To run Maven on a Windows agent, use
            // bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         
         }
      }
   }


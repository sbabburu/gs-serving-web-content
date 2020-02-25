pipeline {
   agent any

    stages {
      stage('Build') {
         steps {
            
           
            // Run Maven on a Unix agent.
            
            sh "mvn clean install -f /var/lib/jenkins/workspace/java-k8s/complete/pom.xml"

            // To run Maven on a Windows agent, use
            // bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         
         }
      }
   }


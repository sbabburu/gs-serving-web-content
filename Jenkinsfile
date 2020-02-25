pipeline {
   agent any
        environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
      stage('Build') {
         steps {
            
           
            // Run Maven on a Unix agent.
            
            sh "mvn clean install -f /var/lib/jenkins/workspace/java-k8s/complete/pom.xml"

            // To run Maven on a Windows agent, use
            // bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         
         }
       
       
        stage('Build Docker Image'){
            steps{
                sh "docker build -f/var/lib/jenkins/workspace/java-k8s/complete/Dockerfile -t sbabburu/springjava-app:${DOCKER_TAG} "
            }
        }
        stage('DockerHub Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_login', passwordVariable: 'passwd', usernameVariable: 'username')]) {
                     sh "docker push sbabburu/springjava-app:${DOCKER_TAG}"
                }
            }
        
       
      }
   }
}
def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

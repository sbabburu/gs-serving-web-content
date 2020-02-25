pipeline {
   agent any
        environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
      stage('Build') {
         steps {
            
            sh "mvn clean install -f /var/lib/jenkins/workspace/java-k8s/complete/pom.xml"
 
         }
         
         }
       
        stage('Build Docker Image'){
            steps{
               sh "docker build -f /var/lib/jenkins/workspace/java-k8s/complete -t sbabburu/springjava-app:${DOCKER_TAG}"
            }
        }
        stage('DockerHub Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_login', passwordVariable: 'passwd', usernameVariable: 'username')]) {
                     sh "docker push sbabburu/springjava-app:${DOCKER_TAG}"
                }
            }   }
   }
}
def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

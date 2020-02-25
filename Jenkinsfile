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
       
        stage('DeployToProduction') {
            
            steps {
                input 'Deploy to Production?'
                milestone(1)
                kubernetesDeploy(
                    kubeconfigId: 'kube-config',
                    configs: 'pods.yml',
                    enableConfigSubstitution: true
                )
            }
        }
        
   }
}
def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}

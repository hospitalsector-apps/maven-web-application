node{
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('')])])

echo "The Job name is: ${env.JOB_NAME}"
echo "The Nod ename is: ${env.NODE_NAME}"
echo "The Build Number is: ${env.BUILD_NUMBER}"
echo"The Jenkins Home directory is: ${JENKINS_HOME}"

def mavenHome = tool name: "maven3.8.6"

stage( 'CheckoutCode' ){
git branch: 'development', credentialsId: '266a6eaa-7043-46cd-afac-f5caef7bce8e', url: 'https://github.com/hospitalsector-apps/maven-web-application.git'
}

stage(' Build' ){
sh  "${mavenHome}/bin/mvn clean package"  
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployAppIntoTomcatServer'){
sshagent(['cf3b31e0-d288-4a0b-956f-390f00e9ca10']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@43.205.240.75:/opt/apache-tomcat-9.0.70/webapps/"
}
}

*/

}

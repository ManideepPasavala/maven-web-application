node{
    
def mavenHome = tool name: "Maven3.8.4"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
   
stage('checkoutCode')
{
git branch: 'development', credentialsId: 'eaa29421-518a-41c4-8037-a281fa9bf3f5', url: 'https://github.com/ManideepPasavala/maven-web-application.git'
}

stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReprt')
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('UploadArtifactIntoNexus')
{
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployAppIntoTomcatServer')
{
sshagent(['89611027-8ca7-4e3c-b20a-8fba9d7c5e83']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.43.26:/opt/apache-tomcat-9.0.63/webapps"
}

}

*/
}

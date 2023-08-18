node{

echo "Jenkins Home Directory is: ${env.JENKINS_HOME}"
echo "Job name is: ${env.JOB_NAME}"
echo "Build number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: 'maven-3.9.3'
stage('CheckOutCode'){

git branch: 'development', credentialsId: '271407d7-2f5d-4cac-93d6-03523b1ad7a3', url: 
'https://github.com/Githubtestspace/maven-web-application.git'

}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubereport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('Uploadartifactsintonexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployappintoTomcatserver'){

sshagent(['1e9fa735-2e70-4e95-83e4-0b61ee95c12e']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.2.111:/opt/apache-tomcat-9.0.76/webapps/"
   
}
}
*/
}

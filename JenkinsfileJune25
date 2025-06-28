node {

def mavenHome = tool name: "maven3.9.9" 

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("Get the code from GitHub"){
git branch: 'development', credentialsId: 'GitHub Creds', url: 'https://github.com/santoshvivan/maven-web-application.git'
}
  
stage ("Build the package in maven"){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage ("Generate SonarQube Report"){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Upload artifact into Nexus Repo"){
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy the application into Tomcat Server"){
sshagent(['Tomcat Linux Creds']) {
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@10.10.2.48:/opt/apache-tomcat-9.0.106/webapps" 	
}
}

stage ("Send email notification"){
mail bcc: '', body: '''Build Status ...............

Thanks
Santosh Panchal''', cc: '', from: '', replyTo: '', subject: 'Build Status......', to: 'panchal.santosh1986@gmail.com'
}
*/
}

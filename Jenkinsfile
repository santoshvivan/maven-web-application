node {

def mavenHome = tool name: "maven3.9.9"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("Get the code from Github"){
git branch: 'development', credentialsId: 'Github Credentials', url: 'https://github.com/santoshvivan/maven-web-application.git'
}
/*
stage ("Build the maven package"){
sh "${mavenHome}/bin/mvn clean package"
}

stage ("Generating sonarqube report"){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Upload artifact into nexus repo"){
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy application to tomcat"){
sshagent(['Tomcat Creds']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@10.10.10.168:/opt/apache-tomcat-9.0.109/webapps'    
}
}

stage ("Send email notification"){
emailext body: '''Build Status.......

Thanks
Santosh Panchal''', subject: 'Build Status.......', to: 'panchal.santosh1986@gmail.com'
}
*/
}

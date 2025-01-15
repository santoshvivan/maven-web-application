node{

def mavenHome = tool name: "maven3.9.0"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("Get the code from GitHub"){
git branch: 'development', credentialsId: '45d65bab-5315-4e98-92e7-a84046d92178', url: 'https://github.com/santoshvivan/maven-web-application.git'
}

stage ("Build the package in Maven"){
sh "${mavenHome}/bin/mvn clean package"
}

stage ("Generate SonarQube Report"){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("Copy Artifact Into Nexus Repo"){
sh "${mavenHome}/bin/mvn deploy"
}

stage ("Deploy App In Tomcat")
sshagent(['568034ac-132c-427c-8d58-c148b3edb468']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.6.37.125:/opt/apache-tomcat-9.0.97/webapps'
}

stage ("Email Notification"){
emailext body: '''Build Status.....

Thanks
Santosh''', subject: 'Build Status....', to: 'panchal.santosh1986@gmail.com'
}

}

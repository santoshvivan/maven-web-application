node{

def mavenHome = tool name: "maven3.9.1"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3')), pipelineTriggers([pollSCM('* * * * *')])])

stage ("get the code from github"){
git branch: 'development', credentialsId: '9d586cbb-8588-4791-8ed9-37f5a78f7a27', url: 'https://github.com/santoshvivan/maven-web-application.git'
}

stage ("build the maven package"){
sh "${mavenHome}/bin/mvn clean package"
}

stage ("executing the sonarqube report"){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage ("upload artifact into nexus repository"){
sh "${mavenHome}/bin/mvn deploy"
}

stage ("deploy app in tomcat"){
sshagent(['7b353228-1b88-44bd-a23b-12f9201fc191']) {
    sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.111.157.61:/opt/apache-tomcat-9.0.102/webapps'
}
}

stage ("email notification"){
emailext body: '''Build Over....
Thanks
Santosh Panchal''', subject: 'Build Over.....', to: 'panchal.santosh1986@gmail.com'
}

}

node
{

def mavenHome = tool name: "maven3.9.0"

stage ("Get the code from GitHub"){
git branch: 'development', credentialsId: '782eb40d-250d-4618-8713-935a737fe019', url: 'https://github.com/santoshvivan/maven-web-application.git'
}

stage ("Build the package in Maven"){

sh "${mavenHome}/bin/mvn clean package"

}
/*
stage ("Generate SonarQube Report"){

sh "${mavenHome}/bin/mvn sonar:sonar"

}

stage ("Upload package into Nexus"){

sh "${mavenHome}/bin/mvn deploy"

}

stage ("Deploy application into Tomcat"){

sshagent(['debca62c-3cbf-4dc9-8b52-2eb514fa1e63']) {
sh 'scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.174.148:/opt/apache-tomcat-9.0.89/webapps'
}
}

stage ("Send Email Notification"){
emailext body: '''Build Over........

Thanks
Santosh''', subject: 'Build Over........', to: 'panchal.santosh1986@gmail.com'
}

*/
}

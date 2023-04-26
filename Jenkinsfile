node{
  stage('SCM Checkout'){
    git 'https://github.com/Nikitakumari13/Deploy_War'
  }
  stage('compile-package'){
    // Get maven home path
    def mvnHome = tool name: 'mavan3', type: 'maven'
    sh "${mvnHome}/bin/mvn package" 
  }
  //stage('Email Notification'){}
  
  stage('Deploy to Tomcat'){
  
    sshagent(['tomcat-dev']) {
    sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.7.211:/home/ec2-user/tomcat/webapps'
}
  }
}

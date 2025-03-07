pipeline{
 agent any
  tools{
    maven 'mymaven'
 }
triggers {
pollSCM('* * * * *') 
  }
stages{
   stage('Checkout Code')
        {
            steps{
                git branch:'main' url:'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
     stage('compile code') {
         steps{
            sh 'mvn compile'
          }
     }
      stage('test code') {
         steps{
       sh 'mvn test'
          }
     }
      stage('build code') {
         steps{
            sh 'mvn package'
          }
     }
    stage('deplot code'){
          steps{
          deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://3.86.159.107:9090/')], contextPath: null, war: '**/*.war'
          }
}

}

}

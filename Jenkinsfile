pipeline{
agent any
  tools{
     maven 'mymaven'
  }

stages{
stage('clone Repo')
  {
    steps{
       git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'     
    }
  }
stage('Build Code')
  {
    steps{
       sh 'mvn package'   
    }
  }

stage('Deploy Code')
  {
    steps{
      deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://54.162.57.140:8080/')], contextPath: null, war: '**/*.war'
    }
  }
}

  
}

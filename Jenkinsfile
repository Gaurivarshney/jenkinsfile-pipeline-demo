pipeline{
agent any
tool name: 'Nodejs', type: 'nodejs'

stages{
stage('clone Repo')
  {
    steps{
       git 'https://github.com/Gaurivarshney/FoodDelivery_MERN.git'     
    }
  }
stage('Install Dependencies') {
            steps {
                sh '''
                cd frontend && npm install
                cd ../backend && npm install
                '''
            }
        }

        stage('Build Frontend') {
            steps {
                sh '''
                cd frontend
                npm run build
                cp -r build ../backend/public
                '''
            }
        }

        stage('Package WAR (for Tomcat)') {
            steps {
                sh '''
                mkdir -p package
                cp -r backend/* package/
                jar cvf mern-app.war -C package/ .
                '''
            }
        }

stage('Deploy Code')
  {
    steps{
      deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://3.86.159.107:9090/')], contextPath: null, war: '**/*.war'
    }
  }
}

  
}

pipeline{
    
    agent any  // here any = current available ec2 server where jenkins is installed
    
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
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        stage('Compile Code'){
            steps{
                echo "compiling the code...."
                sh 'mvn compile'
            }
        }
        stage('Test code'){
            steps{
                echo "testing the code using maven surefire"
                sh 'mvn test'
            }
        }
        
        stage('BuildCode'){
            steps{
                echo "generating artifact..."
                sh 'mvn package'
            }
        }
        
    }
    
    
    
}












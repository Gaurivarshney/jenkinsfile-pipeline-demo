pipeline {
    agent any
    tools {
        maven 'mymaven'  // Ensure 'mymaven' is configured in Global Tool Configuration
    }
    triggers {
        pollSCM('H/5 * * * *')  // Poll every 5 minutes instead of every minute
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }

        stage('Compile Code') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test Code') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Build Code') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy Code') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcatCredentials',
                        path: '',
                        url: 'http://3.86.159.107:9090/'
                    )
                ], contextPath: '/your-app', war: '**/*.war'
            }
        }
    }
}

pipeline {
    agent any
    environment {
        NODE_VERSION = '22.8.0'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Gaurivarshney/FoodDelivery_MERN.git'
            }
        }
        stage('Install Node') {
            steps {
                sh 'node -v || nvm install ${NODE_VERSION}'
            }
        }
        stage('Build Frontend') {
            steps {
                dir('client') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Build Backend') {
            steps {
                dir('server') {
                    sh 'npm install'
                    sh 'npm start'
                }
            }
        }
       stage('deploy code') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://3.86.159.107:9090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

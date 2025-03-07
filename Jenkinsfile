pipeline{
    agent any
    tools{
        nodejs 'Nodejs'
    }
    stages{
        stage('CLone'){
            steps{
                git 'https://github.com/Gaurivarshney/React_Ecom_Website.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    echo 'Installing project dependencies...'
                    sh 'npm install'
                }
            }
        }
        stage('Build Project') {
            steps {
                script {
                    echo 'Building the React app...'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying the app...'
                    // Replace with your deployment steps
                    sh 'cp -r build/* /var/www/html/react-ecom/'
                }
            }
        }
    }

    }


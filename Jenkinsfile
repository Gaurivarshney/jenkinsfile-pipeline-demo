pipeline{
    agent any
    tool name: 'Nodejs', type: 'nodejs'
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

        stage('Run Tests') {
            steps {
                script {
                    echo 'Running tests...'
                    sh 'npm test'
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
}

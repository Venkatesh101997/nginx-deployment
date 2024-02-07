pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code from GitHub'
                git 'https://github.com/Venkatesh101997/nginx-deployment.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies using npm'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application (add your build steps here)'
                // Add build steps if needed
            }
        }

        stage('Deploy to Nginx') {
            steps {
                echo 'Copying files to Nginx path'
                // Copy files to Nginx path (adjust paths accordingly)
                sh 'rsync -av --delete ./ /usr/share/nginx/'
            }
        }

        stage('Restart Nginx') {
            steps {
                echo 'Restarting Nginx (if needed)'
                // Restart Nginx if needed
                sh 'sudo systemctl restart nginx'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful'
            // Additional success actions or notifications
        }
        failure {
            echo 'Deployment failed'
            // Additional failure actions or notifications
        }
    }
}

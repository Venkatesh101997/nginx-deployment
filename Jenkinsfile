pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from GitHub
                git url: 'https://github.com/Venkatesh101997/nginx-deployment.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies using npm for Node.js projects
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                // Add build steps if needed
            }
        }

        stage('Deploy to Nginx') {
            steps {
                // Copy files to Nginx path (adjust paths accordingly)
                script {
                    sh 'rsync -av --delete ./ /usr/share/nginx/'
                }
            }
        }

        stage('Restart Nginx') {
            steps {
                // Restart Nginx if needed
                script {
                    sh 'sudo systemctl restart nginx'
                }
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

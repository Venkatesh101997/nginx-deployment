pipeline {
    agent any

    environment {
        // Define the NodeJS tool installation named 'nodejs'
        nodejs = tool 'NodeJS'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Your Git checkout step with explicit branch (e.g., main)
                    git branch: 'main', url: 'https://github.com/Venkatesh101997/nginx-deployment.git'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Set the NPM registry if needed
                    sh 'npm config set registry https://registry.npmjs.org/ --timeout=120000'
                    
                    // Install dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Assuming NGINX path is /usr/share/nginx/html
                    def nginxPath = '/usr/share/nginx/html'

                    // Copy application files to NGINX path
                    sh "cp -r * ${nginxPath}/"
                }
            }
        }
    }

    post {
        always {
            // Clean up any temporary files or perform other cleanup tasks
        }
    }
}

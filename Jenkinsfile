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
                    // Your Git checkout step for a public repository
                    git url: 'https://github.com/Venkatesh101997/nginx-deployment.git'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Change to the directory where your package.json is located
                    dir('path/to/your/app') {
                        // Run npm install to install dependencies
                        sh "${env.BUILD_ID} npm install"
                    }
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Customize your build and deploy steps here
                    // For example, you can use 'npm run build' or other build commands

                    // Assuming you have an Nginx server running, copy files to the Nginx web root
                    sh "cp -r path/to/your/app /usr/share/nginx/html"
                }
            }
        }
    }
}

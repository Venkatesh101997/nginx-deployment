pipeline {
    agent any
    
    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Your build steps here
                    echo 'Building...'
                }
            }
        }

        stage('Install Nginx and Deploy') {
            steps {
                script {
                    // Install Nginx based on the package manager of your Linux distribution
                    sh 'sudo yum install -y nginx'  // For CentOS/RHEL
                    // OR
                    // sh 'sudo apt-get update && sudo apt-get install -y nginx'  // For Debian/Ubuntu

                    // Deploy to the default Nginx deployment path
                    sh 'cp -r /var/lib/jenkins/workspace/build/* /usr/share/nginx/html/'

                    // Start Nginx
                    sh 'sudo systemctl start nginx'  // Use 'service nginx start' for older systems
                }
            }
        }
    }
    
    post {
        always {
            // Clean up workspace after the build
            cleanWs()
        }
    }
}

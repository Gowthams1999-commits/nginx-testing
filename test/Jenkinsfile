pipeline {
    agent {
        docker { image 'nginx:latest' } // Use the latest NGINX Docker image
    }
    stages {
        stage('Run NGINX') {
            steps {
                script {
                    // Run NGINX in detached mode
                    sh 'docker run -d --name my-nginx -p 8080:80 nginx:latest'
                    
                    // Optional: Verify NGINX is running
                    sh 'docker ps'
                }
            }
        }
    }
    post {
        always {
            // Cleanup the container after the pipeline is done
            script {
                sh 'docker stop my-nginx || true'
                sh 'docker rm my-nginx || true'
            }
        }
    }
}

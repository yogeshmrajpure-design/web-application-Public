pipeline {
    agent any

    // Use environment variables to make the script easy to update
    environment {
        IMAGE_NAME = "css-project-image"
        CONTAINER_NAME = "css-container"
        EXTERNAL_PORT = "3000"
    }

    stages {
        // Stage 1: Checkout is performed automatically by Jenkins
        
        stage('Docker Build') {
            steps {
                echo "Building Docker Image..."
                // Using the '.' assumes the Dockerfile is in the root
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Docker Deploy') {
            steps {
                echo "Deploying to Port ${EXTERNAL_PORT}..."
                sh '''
                    # Stop and remove the container if it's already running
                    docker stop ${CONTAINER_NAME} || true
                    docker rm ${CONTAINER_NAME} || true
                    
                    # Run the new container
                    # We map host port 3000 to Nginx container port 80
                    docker run -d -p ${EXTERNAL_PORT}:80 --name ${CONTAINER_NAME} ${IMAGE_NAME}
                '''
            }
        }
    }

    post {
        success {
            echo "Successfully deployed! Access your site at http://<your-aws-ip>:${EXTERNAL_PORT}"
        }
        failure {
            echo "Pipeline failed. Check the console output for errors."
        }
    }
}

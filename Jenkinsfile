pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "raghava1329/dstest:v5"
    }

    stages {
        stage("Build") {
            steps {
                echo 'Building the application in main'
            }
        }

        stage("Test") {
            steps {
                echo 'Testing the application in main'
            }
        }

        stage("Deploy with Docker") {
            steps {
                script {
                    echo "Pulling Docker image from Docker Hub..."
                    sh "docker pull ${DOCKER_IMAGE}"

                    echo "Stopping old container (if exists)..."
                    sh "docker rm -f myapp_container || true"

                    echo "Running new container..."
                    sh """
                        docker run -d --name myapp_container -p 8081:5050 ${DOCKER_IMAGE}
                    """
                }
            }
        }
    }
}

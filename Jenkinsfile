pipeline {
    agent any

    environment {
        DOCKER_REGISTRY = "docker.io"
        IMAGE_NAME = "back_end/python3"
        IMAGE_TAG = "latest"
        DOCKER_CREDENTIALS = "docker"
    }

    triggers {
        // Automatically trigger the build when a push event happens in GitHub
        githubPush()  // Triggers build via GitHub webhook
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'git', url: 'https://github.com/chan-269/docker-course-three-tier-web-app.git'
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker images for API, App, and DB
                    def image = docker.build("docker.io/chandanuikey97/backup_api:latest", "./api")
                    docker.withRegistry('https://index.docker.io/v1/', "docker") {
                        image.push()
                    }

                    def front_image = docker.build("docker.io/chandanuikey97/backup_app:latest", "./app")
                    docker.withRegistry('https://index.docker.io/v1/', "docker") {
                        front_image.push()
                    }

                    def db_image = docker.build("docker.io/chandanuikey97/backup_db:latest", "./db")
                    docker.withRegistry('https://index.docker.io/v1/', "docker") {
                        db_image.push()
                    }
                }
            }
        }

        // Optionally, you can add a cleanup step to remove unused Docker images
        // stage('Cleanup') {
        //     steps {
        //         sh 'docker system prune -f'
        //     }
        // }
    }

    // Post actions
    post {
        success {
            echo "Docker images pushed successfully."
        }
        failure {
            echo "Pipeline failed."
        }
    }
}
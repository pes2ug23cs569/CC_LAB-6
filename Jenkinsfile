pipeline {
    agent any

    stages {

        stage('Build Backend Image') {
            steps {
                script {
                    docker.build("backend-image", "backend/")
                }
            }
        }

        stage('Run Backend Container') {
            steps {
                script {
                    docker.image("backend-image").run("-d --name backend-container")
                }
            }
        }

        stage('Run NGINX Container') {
            steps {
                script {
                    docker.image("nginx").run("-d -p 8081:80 --name nginx-container -v /nginx/default.conf:/etc/nginx/conf.d/default.conf")
                }
            }
        }
    }
}

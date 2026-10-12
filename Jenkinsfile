pipeline {
    agent any
    environment {
        // Hapus variabel PATH Linux dan DOCKER_HOST linux agar tidak memicu error docker.sock
        IMAGE_NAME = 'abdieeuh/simple-app'
        REGISTRY = 'https://index.docker.io/v1/'
        REGISTRY_CREDENTIALS = 'dockerhub-credentials'
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Melakukan checkout dari SCM...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Mulai build aplikasi'
                bat 'echo "Build selesai ✅"'
            }
        }
        stage('Push Docker Image') {
            steps {
                echo 'Mendorong Docker image...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                    bat 'docker push abdieeuh/simple-app:11'
                }
            }
        }
        }
        stage('Push Docker Image') {
            steps {
                echo 'Mendorong Docker image...'
                bat 'docker push abdieeuh/simple-app:11'
            }
        }
    }
    post {
        always {
            echo 'Selesai build 🏁OYYY'
        }
    }
}

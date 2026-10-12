pipeline {
    agent any
    environment {
        IMAGE_NAME = 'wildanleroy/simple-app'
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
        stage('Build Docker Image') {
            steps {
                echo 'Membangun Docker image...'
                // Ubah nama image sesuai dengan akun Docker Hub Anda
                bat 'docker build -t "wildanleroy/simple-app:11" .'
            }
        }
        stage('Push Docker Image') {
            steps {
                echo 'Mendorong Docker image...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                    // Push dengan nama image yang baru
                    bat 'docker push wildanleroy/simple-app:11'
                }
            }
        }
    }
    post {
        always {
            echo 'Selesai build 🏁OYYY'
        }
    }
}

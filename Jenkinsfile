pipeline {
    agent any
    environment {
        IMAGE_NAME = 'abdieeuh/simple-app'
        REGISTRY = 'https://index.docker.io/v1/'
        REGISTRY_CREDENTIALS = 'dockerhub-credentials'
        PATH = "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
        DOCKER_HOST = "unix:///var/run/docker.sock"
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
                // Menjalankan build langsung via CMD Windows
                bat 'docker build -t "abdieeuh/simple-app:11" .'
                }
            }
        }
       stage('Push Docker Image') {
          steps {
            echo 'Mendorong Docker image...'
            // Menjalankan push langsung via CMD Windows
            bat 'docker push abdieeuh/simple-app:11'
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

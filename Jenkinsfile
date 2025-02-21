pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/aman8702/springboot.git'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/aman8702/springboot.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh './mvnw clean package'
            }
        }

        stage('Test Application') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Archive Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-spring-boot-app:latest .'
            }
        }
    }
}

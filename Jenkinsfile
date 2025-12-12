pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {
        stage('Build Contracts') {
            steps {
                sh 'cd books-api-contract && mvn install -DskipTests'
                sh 'cd events-contract && mvn install -DskipTests'
            }
        }

        stage('Build Services') {
            steps {
                sh 'cd analytics-service && mvn clean package -DskipTests'
                sh 'cd audit-service && mvn clean package -DskipTests'
                sh 'cd demo-rest && mvn clean package -DskipTests'
                sh 'cd ws && mvn clean package -DskipTests'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker compose up --build -d'
            }
        }
    }
}
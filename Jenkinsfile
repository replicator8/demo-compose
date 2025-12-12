pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker compose up --build -d'
            }
        }
    }
}
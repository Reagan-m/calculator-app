pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/Reagan-m/calculator-app.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t calculator-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f calculator-app || true
                docker run -d --name calculator-app -p 8080:6000 calculator-app
                '''
            }
        }
    }
}


pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Reagan-m/simple-calc.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build || echo "No build step"'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t simple-calc-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name simple-calc -p 6000:6000 simple-calc-app'
            }
        }
    }
}

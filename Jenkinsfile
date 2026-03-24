pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/MariaMitrikeska/kiii-jenkins-pipeline.git'
            }
        }

        stage('Build image') {
            steps {
                sh 'docker build -t my-nginx-app .'
            }
        }

        stage('Push image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'docker login -u $USER -p $PASS'
                    sh 'docker push my-nginx-app'
                }
            }
        }
    }
}

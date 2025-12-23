pipeline {
    agent any

    stages {
        stage('코드 가져오기') {
            steps {
                git 'https://github.com/yechanb219-dot/ci-cd-demo.git'
            }
        }

        stage('도커 이미지 만들기') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('서버에서 실행하기') {
            steps {
                sh '''
                docker rm -f my-app || true
                docker run -d -p 80:8080 --name my-app my-app
                '''
            }
        }
    }
}

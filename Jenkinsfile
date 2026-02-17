pipeline {
    agent any

    stages {
        stage('Clone git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/fernandobortolanzza/jk-public-gh.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}

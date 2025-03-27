pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image10 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 rajgangasani/paytm:bank'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push rajgangasani/paytm:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 rajgangasani/paytm:bank'
            }
        }
    }
}

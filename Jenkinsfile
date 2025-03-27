pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image12 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 rajgangasani/paytm:movie'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push rajgangasani/paytm:movie'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 rajgangasani/paytm:movie'
            }
        }
    }
}

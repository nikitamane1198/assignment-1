pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def app = docker.build("housing-price-prediction")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image("housing-price-prediction").inside {
                        sh 'python -m unittest discover -s tests'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.image("housing-price-prediction").run('-p 80:80')
                }
            }
        }
    }
}

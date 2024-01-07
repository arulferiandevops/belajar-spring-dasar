pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build 7'
            }
        }

        stage('Test') {
            steps {
                echo 'Hello Test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Hello Deploy'
            }
        }
    }

    post {
        always {
            echo "I will always say hello again"
        }
        success {
            echo "yay, success"
        }
        failure {
            echo "oh no, failure"
        }
        cleanup {
            echo "dont care success or error"
        }
    }
}
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    for (int i=0; i<10; i++) {
                        echo("Script ${i}")
                    }
                }
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build'
                echo 'Hello Build 7'
                sh("./mvnw clean compile test-compile")
            }
        }

        stage('Test') {
            steps {
                echo 'Hello Test'
                sh("./mvnw test")
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
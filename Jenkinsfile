pipeline {
    agent any
    environment {
        AUTHOR = "Arul Ferian Ramadloni"
        EMAIL = "arulferianramadloni@gmail.com"
    }
    stages {
        stage('Prepare') {
            steps {
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch Name : ${env.BRANCH_NAME}")
            }
        }
        stage('Build') {
            steps {
                script {
                    for (int i=0; i<10; i++) {
                        echo("Script ${i}")
                    }
                }
                echo 'Hello Build'
                echo("Author ${AUTHOR}")
                echo("Email ${EMAIL}")
                sh("./mvnw clean compile test-compile")
            }
        }

        stage('Test') {
            steps {
                script {
                    def data = [
                        "firstname": "Arul",
                        "lastname": "Ferian"
                    ]
                    writeJSON(file:"data.json", json: data)
                }
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
pipeline {
    agent any
    environment {
        AUTHOR = "Arul Ferian Ramadloni"
        EMAIL = "arulferianramadloni@gmail.com"
    }
    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "What is yout name")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "What is yout name")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "Mau dideploy?")
        choice(name: "SOCIAL_MEDIA", choices: ['Instagram', 'Fb', 'X'], description: "What is yout name")
        password(name: "SECRET", defaultValue: "", description: "What is yout name")
    }
    stages {
        stage("paramater") {
            steps{
                echo("name : ${params.NAME}")
                echo("you are : ${params.DESCRIPTION}")
                echo("your social media : ${params.SOCIAL_MEDIA}")
                echo("need to deploy? : ${params.DEPLOY}")
                echo("password : ${params.SECRET}")
            }
        }
        stage('Prepare') {
            environment {
                APP = credentials("arul")
            }
            steps {
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch Name : ${env.BRANCH_NAME}")
                echo("APP User : ${APP_USR}")
                echo("APP Password : ${APP_PSW}")
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
            input {
                message "Can we deploy?"
                ok "Yes. silakan"
                submitter "arulferiandevops"
                parameters {
                    choice(name: "TARGET_ENV", choices:['DEV','QA','PROD'], description: "Mau didpeloy dimana?")
                }
            }
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
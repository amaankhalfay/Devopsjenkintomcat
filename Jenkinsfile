pipeline {
    agent any

    tools {
    maven 'maven-3.9.12'
    jdk 'jdk-25'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/amaankhalfay/DevOps4.git'
                 
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'hello-world',
                war: 'target/hello-world.war'
            }
        }
    }
}

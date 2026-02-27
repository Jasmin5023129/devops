pipeline {
    agent any

    tools {
    maven 'Maven-3.9.12'
    jdk 'jdk-21'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Jasmin5023129/devops.git'
                 
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
                contextPath: 'hello-world3',
                war: 'target/hello-world3.war'
            }
        }
    }
}

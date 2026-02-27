pipeline {
    agent any

    tools {
    maven 'maven'
    jdk 'jdk-21'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/itdep202427-cmd/DEVOPS-4.git'
                 
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
                contextPath: 'hello-world2',
                war: 'target/hello-world2.war'
            }
        }
    }
}

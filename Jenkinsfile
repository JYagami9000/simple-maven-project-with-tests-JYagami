pipeline {
    agent any

    tools {
        maven 'Maven'   // Must match the name configured in Jenkins Global Tool Configuration
        jdk 'JDK'       // Must match your configured JDK name
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}

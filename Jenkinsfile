pipeline {
    agent any

    tools {
        maven 'Maven'   // Same Maven tool name configured in Jenkins
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master',
                url: 'https://github.com/RashiSaraswat/mymavenseleniumapp01.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Selenium Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Generate Test Report') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }

    post {
        success {
            echo 'Selenium tests executed successfully!'
        }

        failure {
            echo 'Build or tests failed!'
        }

        always {
            archiveArtifacts artifacts: 'target/**/*.html', allowEmptyArchive: true
        }
    }
}

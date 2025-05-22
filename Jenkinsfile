pipeline {
    agent any

    tools {
        maven 'M3' // Use the Maven tool you configured
    }

    environment {
        GIT_SSH_CREDENTIALS_ID = 'git-ssh-key' // Your SSH credentials ID
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'git@github.com:Mourya595/war-web-project.git',
                    credentialsId: "${env.GIT_SSH_CREDENTIALS_ID}",
                    branch: 'master' // or use 'master' if that's your default
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive WAR File') {
            steps {
                archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }
    }
}

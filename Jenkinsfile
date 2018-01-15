pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving..'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy to staging') {
            steps {
                build job: 'maven-pipeline-staging'
            }
        }
    }
}
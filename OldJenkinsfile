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
        stage('Deploy to production') {
            steps{
                timeout(time:5, unit:'DAYS') {
                    input message: 'Approve PRODUCTION Deployment?'
                }
                build job: 'maven-pipeline-production'
            }
            post {
                success {
                    echo 'Code deployed to production'
                }
                failure {
                    echo 'Deployment failed'
                }
            }
        }
    }
}
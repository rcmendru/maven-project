pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mv clean package'
            }
            post {
                success {
                    echo 'Now Archiving..'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
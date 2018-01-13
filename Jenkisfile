pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mv clean package'
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
pipeline {
    agent any
    tools {
        maven 'maven3'
        docker 'docker1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker --version'
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}

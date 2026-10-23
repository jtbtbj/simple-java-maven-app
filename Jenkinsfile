pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }


         stage('Test') {
            steps {
                sh 'mvn test'
            }



        post {
            always {
                junit 'target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }

}



   

             
    


         stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
}

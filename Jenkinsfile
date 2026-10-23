pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                docker run --rm \
                  -v "$PWD":/app \
                  -v /home/.m2:/root/.m2 \
                  maven:3-alpine \
                  mvn -B -DskipTests -f /app/pom.xml clean package
                '''
            }
        }
    }
}


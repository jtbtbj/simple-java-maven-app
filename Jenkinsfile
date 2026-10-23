pipeline {
    agent any
    stages {
        stage('查看工作目录内容') {
            steps {
                sh '''
                pwd
                echo "==== 当前目录 ===="
                ls -la
                echo "==== 递归查看所有文件 ===="
                find . -type f
                '''
            }
        }
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

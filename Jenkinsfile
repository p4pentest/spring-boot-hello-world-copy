pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2 -p 8083:8083 --rm --detach --network jenkins' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Deploy') { 
            steps {
                sh 'java -jar target/spring-boot-hello-world-1.0.0.jar' 
            }
        }
    }
}

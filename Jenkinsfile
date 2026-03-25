pipeline {
    agent any
    
    tools {
        maven 'M3'
    }

    stages {
        stage('Compilation') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('execution') {
            steps {
                sh 'java -jar target/mon-projet-java-1.0-SNAPSHOT.jar'
            }
        }
    }
}
post{
    success {
        echo "ca a fonctionné"
        archiveArtifacts artifacts: 'target/mon-projet-java-1.0-SNAPSHOT.jar', fingerprint: true
    }
}

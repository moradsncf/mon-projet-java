pipeline {
    agent { label 'testpipelinemorad' }
    
    tools {
        maven 'M3'
    }

    environment {
        IMG="mon-projet-java:${env.BUILD_ID}"
        CT_name="mon-projet-java-container"
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

    post {
        success {
            echo "ca a fonctionné"
            archiveArtifacts artifacts: 'target/mon-projet-java-1.0-SNAPSHOT.jar', fingerprint: true
        }
    }
}

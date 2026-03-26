pipeline {
    agent { label 'testpipelinemorad' }
    
    tools {
        maven 'M3'
    }

    environment {
        IMG="mon-projet-java:${env.BUILD_NUMBER}"
        CT_name="mon-projet-java-container"
    }
    
    stages {
        stage('Compilation') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build docker image'){
            steps {
                sh "docker build -t ${IMG} ."
            }
        }
        
        stage('deploiment'){
            steps {
                sh "docker stop ${CT_name} || true"
                sh "docker rm ${CT_NAME} || true"
                sh "docker run -d --name ${CT_NAME} ${IMG}"
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

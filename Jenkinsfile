pipeline {
    agent any
    tools {
        maven 'Maven'
        jdk 'Java 8'
    }
    options {
        buildDiscarder(logRotator(artifactNumToKeepStr: '5'))
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'Waterfall-Proxy/bootstrap/target/Waterdog*.jar', fingerprint: true
                }
            }
        }
    }

    post {
        always {
            deleteDir()
        }
    }
}
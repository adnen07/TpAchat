pipeline {
    agent any
     environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "192.168.56.10:8081"
        NEXUS_REPOSITORY = "my-app"
        VERSION = "1.0-SNAPSHOT"
        NEXUS_CREDENTIAL_ID = "f3148557-fc2c-4b43-9630-0baa29917de9"
    }
    stages {
        stage('Clone') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/adnen07/TpAchat.git'
                echo "-------------------Clone Stage Done ------------------------------- "
            }
        }
        stage("Maven Build for test pipeline") {
            steps {
                script {
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }
        }
        stage("Maven Build 2") {
            steps {
                script {
                    pwd()
                }
            }
        }
        stage('Hello') {
            steps {
                echo 'Hello World'
                nexusArtifactUploader artifacts: [[artifactId: 'tpAchatProject', classifier: '', file: 'target/tpAchatProject-1.0.jar', type: 'jar']], credentialsId: 'f3148557-fc2c-4b43-9630-0baa29917de9', groupId: 'com.esprit.examen', nexusUrl: '192.168.56.10:8081/repository/maven-releases/', nexusVersion: 'nexus3', protocol: 'http', repository: 'nexusdeploymentrepo', version: '1.0'
            }
        }
        
    }    

}

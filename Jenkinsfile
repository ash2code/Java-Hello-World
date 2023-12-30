pipeline {
    agent any
    tools {
        maven 'Maven3'
    }

    stages {
        stage('code-build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage("add artifact to nexus") {
            steps {
                script {
                    nexusArtifactUploader artifacts: [[
                        artifactId: 'hello-world',
                        classifier: '', 
                        file: 'target/hello-world-1.0.1.jar', 
                        type: 'jar'
                    ]], 
                    credentialsId: 'nexus-credentials', // Ensure this matches the ID you set in Jenkins
                    groupId: 'com.example', 
                    nexusUrl: 'http://172.31.14.165:8081', // Ensure correct URL and port
                    nexusVersion: 'nexus3',
                    protocol: 'http', 
                    repository: 'http://13.201.82.132:8081/repository/hello-world/', 
                    version: '1.0.1'
                }
            }
        }
    }
}

pipeline {
    agent any
    tools {
        maven 'M3'
    }

    stages {
        stage('code-build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}

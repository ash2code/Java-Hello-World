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
        stage('sonar-analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}

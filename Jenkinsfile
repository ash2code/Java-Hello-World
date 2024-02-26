pipeline {
    agent any
    tools {
        maven 'Maven3' // Assuming 'Maven3' is the name of your Maven tool installation in Jenkins
    }
    stages {
        stage('scm-checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, 
                    url: 'https://github.com/ash2code/Java-Hello-World.git'
            }
        }
        stage('code-build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('sonar-analysis') {
            steps {
                withSonarQubeEnv('sonar-api') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}


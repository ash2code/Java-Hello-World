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
        sh 'mvn clean verify sonar:sonar \
          -Dsonar.projectKey=hello-java \
          -Dsonar.projectName=hello-java \
          -Dsonar.host.url=http://44.204.148.6:9000 \
          -Dsonar.token=sqp_d3d08fe0a3082fd586ff13b276b0cb2dd592e5ed'
      }
    }
  }
}

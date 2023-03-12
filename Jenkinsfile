pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git 'https://github.com/gowraajay/mavenrepo.git'
      }
    }

    stage('Build') {
      steps {
        sh '/usr/share/maven/bin/mvn package'
      }
    }

    stage('QA') {
      steps {
        withSonarQubeEnv(envOnly: true, installationName: 'SonarQube', credentialsId: 'SonarToken') {
          sh '/usr/share/maven/bin/mvn clean package sonar:sonar'
        }

      }
    }

  }
}
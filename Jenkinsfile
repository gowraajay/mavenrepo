pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git 'https://github.com/gowraajay/mavenrepo.git'
      }
    }

    stage('Buil & QA') {
      steps {
        withSonarQubeEnv(envOnly: true, installationName: 'SonarQube', credentialsId: 'SonarToken') {
          sh '/usr/share/maven/bin/mvn clean deploy sonar:sonar'
        }

      }
    }

  }
}
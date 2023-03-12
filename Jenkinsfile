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
        withSonarQubeEnv(installationName: 'SonarQube', credentialsId: 'SonarToken1') {
          sh '''\'\'$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$ORGANIZATION \\
        -Dsonar.java.binaries=build/classes/java/ \\
        -Dsonar.projectKey=$PROJECT_NAME \\
        -Dsonar.sources=.\'\''''
        }

      }
    }

  }
}
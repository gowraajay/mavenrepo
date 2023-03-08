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
        sh 'sh \'/usr/local/src/apache-maven/bin/mvn package\''
      }
    }

  }
}
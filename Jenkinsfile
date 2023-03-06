pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: 'master', credentialsId: 'GitToken')
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

  }
}
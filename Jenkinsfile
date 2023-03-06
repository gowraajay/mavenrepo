pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: 'master', credentialsId: 'GitToken')
      }
    }

    stage('Maven') {
      steps {
        build 'Maven Build Life Cycle'
      }
    }

  }
}
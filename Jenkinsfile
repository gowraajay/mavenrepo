pipeline {
  agent none
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: '*/master')
      }
    }

  }
}
pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: '*/master')
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: 'master')
      }
    }

  }
}
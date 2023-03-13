pipeline {
  agent {
    node {
      label 'Dev-Label'
    }

  }
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: 'Master', credentialsId: 'GitToken1')
      }
    }

  }
}
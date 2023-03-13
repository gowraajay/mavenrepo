pipeline {
  agent {
    node {
      label 'Dev-Label'
    }

  }
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/gowraajay/mavenrepo.git', branch: 'master', credentialsId: 'Git1')
      }
    }

    stage('Build') {
      steps {
        sh '/usr/share/maven/bin/mvn package'
      }
    }

    stage('Deploy') {
      steps {
        sh 'scp /root/workspace/oscar_master/target/studentapp-2.5-SNAPSHOT.war 172.31.34.56:/usr/share/apache-tomcat-9.0.63/webapps '
      }
    }

  }
}
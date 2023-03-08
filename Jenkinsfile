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

    stage('Deploy') {
      steps {
        sh 'scp /var/lib/jenkins/workspace/MavenProject_master/target/studentapp-2.5-SNAPSHOT.war 172.31.34.56:/opt/tomcat/webapps'
      }
    }

  }
}
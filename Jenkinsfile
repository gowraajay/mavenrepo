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
        sh '''ssh 172.31.13.59 systemctlfff stop tomcat

scp /var/lib/jenkins/workspace/MavenProject_master/target/studentapp-2.5-SNAPSHOT.war 172.31.13.59:/var/lib/tomcat/webapps

ssh 172.31.13.59 systemctl start tomcat'''
      }
    }

  }
}
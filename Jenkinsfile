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

    stage('QA') {
      steps {
        withSonarQubeEnv(installationName: 'SonarQube', credentialsId: 'SonarToken', envOnly: true) {
          sh '/usr/share/maven/bin/mvn sonar:sonar'
        }

      }
    }

    stage('Deploy Artifact') {
      steps {
        sh '/usr/share/maven/bin/mvn deploy'
      }
    }

    stage('Deploying Artifact into Webserver') {
      steps {
        sh 'scp /root/workspace/TuePro_master/target/studentapp-2.5-SNAPSHOT.war 172.31.34.56:/usr/share/apache-tomcat-9.0.63/webapps '
      }
    }

  }
}
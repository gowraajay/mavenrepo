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

    stage('Mail Notify') {
      steps {
        emailext(subject: 'Project: TuePro Build Success 10 ', body: 'Hello Dev, The Build is success and your artifact is deployed in Nexus and also we have deployed the artifact in WebServer(Tomcat). Regards, DevOpsTeam', attachLog: true, from: 'gowraajay@gmail.com', replyTo: 'gowraajay@gmail.com', to: 'samba81424.sr@gmail.com')
      }
    }

  }
}
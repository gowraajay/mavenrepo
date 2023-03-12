pipeline {
  agent {
    node {
      label 'Dev-Label'
    }

  }
  stages {
    stage('SCM') {
      parallel {
        stage('SCM') {
          steps {
            git 'https://github.com/gowraajay/mavenrepo.git'
          }
        }

        stage('Build') {
          steps {
            sh '/usr/share/maven/bin/mvn clean package'
          }
        }

      }
    }

    stage('Buil & QA') {
      steps {
        withSonarQubeEnv(envOnly: true, installationName: 'SonarQube', credentialsId: 'SonarToken') {
          sh '/usr/share/maven/bin/mvn package sonar:sonar'
        }

      }
    }

    stage('Deploy') {
      steps {
        sh '/usr/share/maven/bin/mvn deploy'
      }
    }

    stage('Mail') {
      parallel {
        stage('Mail') {
          steps {
            emailext(subject: 'Build is Successful', body: 'Hello Dev, The Build got Success and Artifactory is Deployed into the Nexus Repo. For Reports pls login to the nexus', attachLog: true, to: 'gowraajay@gmail.com')
          }
        }

        stage('Deploy Artifact in Tomcat') {
          steps {
            sh 'scp /root/workspace/OpenBlue_master/target/studentapp-2.5-SNAPSHOT.war 172.31.34.56:/usr/share/apache-tomcat-9.0.63/webapps'
          }
        }

      }
    }

  }
}
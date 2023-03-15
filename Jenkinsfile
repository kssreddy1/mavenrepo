pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/kssreddy1/mavenrepo.git', branch: 'master', credentialsId: 'GitHub_Token')
      }
    }

    stage('BUILD') {
      steps {
        sh '/usr/share/maven/bin/mvn clean package'
      }
    }

    stage('QA') {
      steps {
        withSonarQubeEnv(installationName: 'sonar', credentialsId: 'sonar_token', envOnly: true)
        sh '/usr/share/maven/bin/mvn sonar:sonar'
      }
    }

  }
}
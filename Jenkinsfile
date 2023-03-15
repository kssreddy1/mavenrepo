pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/kssreddy1/mavenrepo.git', branch: 'master', credentialsId: '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')
      }
    }

    stage('BUILD') {
      steps {
        sh '/usr/share/maven/bin/mvn clean package'
      }
    }

    stage('QA') {
      steps {
        sh '/usr/share/maven/bin/mvn sonar:sonar'
        withSonarQubeEnv(installationName: 'sonar', credentialsId: 'sonar_token', envOnly: true)
      }
    }

  }
}
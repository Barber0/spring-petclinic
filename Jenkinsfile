node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh "./mvnw clean verify sonar:sonar -Dsonar.projectKey=alpha"
    }
  }
}

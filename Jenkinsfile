node {
  stage('SCM') {
    checkout scm
  }
  environment {
    PATH = "/root/.local/bin:$PATH"
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh './mvnw clean package verify sonar:sonar -Dsonar.projectKey=alpha'
      sh '/root/.local/bin/ansible-playbook ansible-playbook.yml -i ansible/inventory -u root'
    }
  }
}

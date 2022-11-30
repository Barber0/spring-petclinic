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
    }
  }
  ansiblePlaybook(
        playbook: 'ansible-playbook.yml',
        inventory: 'ansible/inventory',
        colorized: true)
}

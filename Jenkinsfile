node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh './mvnw clean package verify sonar:sonar -Dsonar.projectKey=alpha'
    }
  }
  ansiblePlaybook(
        playbook: 'ansible-playbook.yml',
        inventory: 'ansible/inventory',
        credentialsId: 'id_rsa',
        colorized: true)
}

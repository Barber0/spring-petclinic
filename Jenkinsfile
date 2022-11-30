node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh './mvnw clean package verify sonar:sonar -Dsonar.projectKey=alpha'
      sh 'ansible-playbook ansible-playbook.yml -i ansible/inventory -u root --key-file /root/.ssh/id_rsa'
    }
  }
}

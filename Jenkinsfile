pipeline {
  agent { 
     node { 
        label 'jenkins_agent' 
          } 
        } 
   stages {
    stage ('Deploy') {
     steps {
        sh """
           mkdir -p roles
           ansible-galaxy install --force -p roles -r requirements.yml
           ansible-playbook -i inventory playbook.yml --vault-password-file /home/jenkins/vault_pass.txt
           """
           }
      }
     stage ('Test') {
      steps{
        sh """
           ansible-playbook -i inventory test.yml
           """
        }
      }
    }
  }

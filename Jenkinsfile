pipeline {
    agent any
    
    environment {
   ANSIBLE_PRIVATE_KEY=credentials('private-key') 
  }

    stages {
        stage('Git CheckOut') {
            steps {
               git branch: 'main', url: 'https://github.com/jaiswaladi2468/Jenkins-Ansible.git'
            }
        }
        
        stage('Ansible') {
            steps {
               sh "ansible --version"
               sh ''' ansible-playbook -i inventory/hosts -l server playbooks/my-playbook.yml -u root --private-key=$ANSIBLE_PRIVATE_KEY -e "ansible_ssh_common_args='-o StrictHostKeyChecking=no'" '''
            }
        }
    }
}

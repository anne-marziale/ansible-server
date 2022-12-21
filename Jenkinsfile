pipeline {
    agent any 
    stages {
        stage('Installation ansible ubuntu') { 
            steps {
                sh'''
                sudo apt-add-repository ppa:ansible/ansible
                sudo apt update
                sudo apt install ansible
                '''
            }
        }
        stage('Git clone') { 
            steps {
                git 'https://github.com/anne-marziale/ansible-server.git'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'ansible-playbook -i inventory/hosts playbooks/playbook.yml' 
            }
        }
    }
}


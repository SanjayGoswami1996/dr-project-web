pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                // Jenkins automatically pulls the code from the configured GitHub repo
                checkout scm
            }
        }
        stage('Deploy Application & Restart Nginx') {
            steps {
                // Copy the updated HTML files to the Ansible workspace
                sh 'sudo cp index-aws.html index-azure.html /home/ubuntu/ansible-project/app/'
                
                // Run the Ansible playbook you created in Task 3 to deploy and restart services
                sh 'sudo -u ubuntu ansible-playbook -i /home/ubuntu/ansible-project/inventory.ini /home/ubuntu/ansible-project/setup-nginx.yml'
            }
        }
    }
}

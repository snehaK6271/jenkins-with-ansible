pipeline {
  agent { 
  label 'ansible'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
        git credentialsId: '55ffcc7f-9ac2-4c59-99ed-a9aa71b580e7', url: 'https://github.com/snehaK6271/jenkins-with-ansible.git'
      }
    }
     
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat.yml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing

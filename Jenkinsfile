pipeline{
        agent any
        parameters {
  choice choices: ['qa', 'production'], description: 'deploying ruby', name: 'DEPLOY'
}
           stages{

                   stage('Deliver'){
               steps {
        sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY}.ini'
        }
                }
            } 
                   
                   stage('Build'){
                   steps{
                      sh 'ruby main.rb'
                        }
                 }

       }
}

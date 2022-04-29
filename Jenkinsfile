pipeline{
        agent any
        parameters {
  choice choices: ['qa', 'production', 'clude'], description: 'deploying ruby', name: 'DEPLOY'
                
                			string(name: 'upstreamJobName',
          			defaultValue: '',
          			description: 'The name of the job the triggering upstream build'
    				)
}
           stages{

              stage('Deliver'){
               steps {
        sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY_TO}.ini  playbook.yml'
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

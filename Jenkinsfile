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
 		  stage('Copy artifact'){
                 steps {
        copyArtifacts filter: 'sample-ruby', fingerprintArtifacts: true,
          projectName: 'ruby', selector: lastSuccessful()
      }
 }
              stage('Deliver'){
               steps {
        sshagent(['vagrant-private-key']) {
          sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY}.ini  playbook.yml'
        }
                }
              }  
                   stage('Build'){
                   steps{
                      sh 'ruby main.rb'
                        }
                 }
                   
                   	          stage('Docker login'){
                 steps {
			 withCredentials([usernamePassword(credentialsId: 'devops-docker-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
               		  sh 'docker login --username ${USERNAME} --password ${PASSWORD}'
                      }
		    }
                 }
	          stage('Docker build'){
                 steps{
                  sh 'docker build . --tag altubiisraa97/devops:${BUILD_ID}'
                      }		     
                 }
	          stage('Docker push'){
                 steps{
		     sh 'docker push altubiisraa97/devops:${BUILD_ID}'
                      }
                 }

       }
}

pipeline{
        agent any
	stages{
		stage('Build'){
                 steps{
                      sh 'go build -o sample1 main.go'
                        }
                 }

// 		parameters {
//   		 choice choices: ['qa', 'production'], description: 'Select environment for deployment', name: 'DEPLOY_TO'
// 			string(name: 'upstreamJobName',
//           			defaultValue: '',
//           			description: 'The name of the job the triggering upstream build'
//     				)		
// 		}

//             stages{
//  		  stage('Copy artifact'){
//                  steps {
//         copyArtifacts filter: 'sample1', fingerprintArtifacts: true,
//           projectName: "sample-multibranch/${params.upstreamJobName}", selector: lastSuccessful()
//       }
//  }
			   
//               stage('Deliver'){
//                steps {
//         sshagent(['vagrant-private-key']) {
//           sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i ${DEPLOY_TO}.ini playbook.yml'
//         }
//                 }
//             }
      }
}

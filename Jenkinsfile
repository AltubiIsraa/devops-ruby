pipeline{
        agent any
        parameters {
  choice choices: ['qa', 'production'], description: 'deploying ruby', name: 'DEPLOY'
}
           stages{
               stage('Build'){
                   steps{
                      sh 'main.rb'
                        }
                 }

       }
}

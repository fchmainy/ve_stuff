#!/usr/bin/env groovy

import groovy.json.JsonOutput



node {
   stage('Preparation') { 
            git 'https://github.com/fchmainy/ve_stuff.git'   
       
            // Setting up environment variables
            echo "setting up variables..."
            env.ovaname = params.OVAFullName
   }
   
    
   stage('Patch and Send the OVA to vSphere') {
              ansiblePlaybook(
                colorized: true, 
                playbook: 'gitlab_addNewVE.yaml', 
                inventory: 'hosts.ini', 
                limit: 'me',
                extras: '-vvv',
                sudoUser: null,
                extraVars: [
                        F5_OVA: ovaname
              ])
       
   }
}   
//   stage('End of the Job') {
//     input 'Now you can check on your vCenter if the image has been uploaded'
//}

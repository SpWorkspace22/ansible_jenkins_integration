pipeline {
    agent any
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '3')
    }

    stages {
        stage("Test Remote Machine Connection"){
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ansible_vagrant', keyFileVariable: 'ansible_vagrant')]) {
                    ansiColor('xterm') {
                       ansiblePlaybook(credentialsId: 'ansible_vagrant-key', inventory: 'inventory/Development/Dev_Server.yml', playbook: 'module_getent.yml',colorized:true)
                    }
                }
            }
        }
    }
}

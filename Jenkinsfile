pipeline {
    agent any
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '3')
    }

    stages {
        stage("Test Remote Machine Connection"){
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ansible-vagrant', keyFileVariable: 'ansible-connection')]) {
                    ansiColor('xterm') {
                       // ansiblePlaybook(credentialsId: 'ansible-connection-key', inventory: 'inventory/Development/Dev_Server.yml', playbook: 'Host_Test.yml',colorized:true)
                        ansibleAdhoc(credentialsId:'ansible-connection-key',inventory: 'inventory/Development/Dev_Server.yml'', hosts: 'dev_servers', module: 'ping',colorized:true)
                    }
                }
            }
        }
    }
}

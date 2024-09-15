pipeline {
    agent any
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '3')
    }

    stages {
        stage("Test Remote Machine Connection"){
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ansible_vagrant', keyFileVariable: 'ansible_connection', usernameVariable: 'vagrant')]) {
                    ansiColor('xterm') {
                        ansiblePlaybook colorized: true, credentialsId: 'ansible_vagrant', inventory: './inventory/Development/Dev_Server.yml', playbook: './Host_Test.yml', vaultTmpPath: ''
                    }
                }
            }
        }
    }
}

pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    // environment { 
    //     packageVersion = ''
    //     nexusURL = '172.31.37.174:8081'
    // }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'version', defaultValue: '', description: 'what is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'what is the environment?')
    }
    //build
    stages {
        stage('Print version') { 
            steps {
                sh """
                    echo  "version: ${params.version}"
                    echo  "version: ${params.environment}"
                """
            }
        }
    }
    //post build
    post {
        always {
            echo " I will always say Hello again"
            deleteDir()
        }
        failure { 
            echo 'this runs when pipeline is failed, used generally to send some alerts'
        }
        success{
            echo 'I will say Hello when pipeline is success'
        }
    }
}
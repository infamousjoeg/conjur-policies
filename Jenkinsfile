pipeline {
    agent any

    triggers {
        pollSCM '* * * * *'
    }

    environment {
        CONJUR_ACCOUNT = 'cyberarkdemo'
        CONJUR_APPLIANCE_URL = 'https://conjur.joegarcia.dev'
    }

    stages {
        stage('Install cybr-cli') {
            steps {
                sh '''
                wget https://github.com/infamousjoeg/cybr-cli/releases/latest/download/cybr-cli_linux_amd64.tar.gz
                tar -xzf cybr-cli_linux_amd.tar.gz
                chmod +x cybr
                '''
                sh './cybr version'
            }
        }

        stage('Authenticate cybr-cli to Conjur') {
            steps {
                withCredentials([
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-host_ci_jenkins_projects_conjur-policies-username', variable: 'CONJUR_AUTHN_LOGIN'),
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-host_ci_jenkins_projects_conjur-policies-password', variable: 'CONJUR_AUTHN_API_KEY')
                ]) {
                    sh './cybr conjur logon-non-interactive'
                }
            }
        }

        stage('Load Conjur Policies') {
            steps {
                withCredentials([
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-host_ci_jenkins_projects_conjur-policies-username', variable: 'CONJUR_AUTHN_LOGIN'),
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-host_ci_jenkins_projects_conjur-policies-password', variable: 'CONJUR_AUTHN_API_KEY')
                ]) {
                    sh './load_policies.sh > output'
                }
            }
        }
    }
    post {
        always {
            sh '''
                echo "Output from Load Policies script:"
                cat ./output
            '''
        }
    }
}

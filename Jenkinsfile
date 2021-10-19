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
                wget https://github.com/infamousjoeg/cybr-cli/releases/latest/download/linux_cybr -O cybr
                chmod +x cybr
                '''
                sh './cybr version'
            }
        }

        stage('Authenticate cybr-cli to Conjur') {
            steps {
                withCredentials([
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-Application-ConjurUser-httpsconjur.joegarcia.dev-hostcijenkinsprojectsconjur-policies-username', variable: 'CONJUR_AUTHN_LOGIN'),
                    conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-Application-ConjurUser-httpsconjur.joegarcia.dev-hostcijenkinsprojectsconjur-policies-password', variable: 'CONJUR_AUTHN_API_KEY')
                ]) {
                    sh './cybr conjur logon-non-interactive'
                }
            }
        }

        stage('Load Conjur Policies') {
            steps {
                sh './load_policies.sh > output'
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

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
        stage('Configure Conjur Identity') {
            steps {
                sh '''cat << EOF > ~/.conjurrc
                ---
                account: "$CONJUR_ACCOUNT"
                plugins: []
                appliance_url: "$CONJUR_APPLIANCE_URL"
                cert_file: ""
                EOF
                '''
            }
        }

        stage('Create .netrc') {
            steps {
                withCredentials([
                conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-Application-ConjurUser-httpsconjur.joegarcia.dev-hostcijenkinsprojectsconjur-policies-username', variable: 'CONJUR_USERNAME'),
                conjurSecretCredential(credentialsId: 'SyncVault-LOB_CI-D-App-Conjur-Policies-Application-ConjurUser-httpsconjur.joegarcia.dev-hostcijenkinsprojectsconjur-policies-password', variable: 'CONJUR_API_KEY')
                ]) {
                    sh '''cat << EOF > ~/.netrc
                    machine "$CONJUR_APPLIANCE_URL"/authn
                      login "$CONJUR_USERNAME"
                      password "$CONJUR_API_KEY"
                    EOF
                    '''
                }
            }
        }

        stage('Install cybr-cli') {
            steps {
                sh '''
                wget https://github.com/infamousjoeg/cybr-cli/releases/latest/download/linux_cybr -O cybr
                chmod +x cybr
                '''
                sh 'cybr version'
            }
        }

        stage('Authenticate cybr-cli to Conjur') {
            steps {
                sh 'cybr conjur logon-non-interactive'
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

pipeline {
    agent any

    triggers {
        pollSCM ''
    }

    stages {
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

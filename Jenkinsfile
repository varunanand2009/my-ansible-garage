pipeline {
    agent any

    parameters {
        string(
            name: 'USERNAME',
            description: 'Linux username to create on RHEL servers'
        )
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Create User on RHEL Servers') {
            steps {
                sh """
                ansible-playbook \
                -i inventory/hosts \
                playbooks/create_user.yml \
                -e username=${params.USERNAME}
                """
            }
        }
    }
}

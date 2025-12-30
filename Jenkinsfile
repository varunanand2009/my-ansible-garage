pipeline {
    agent any

    parameters {
        string(
            name: 'USERNAME',
            description: 'Linux username to create'
        )
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Debug Workspace') {
            steps {
                sh '''
                echo "===== Workspace content ====="
                pwd
                ls -l
                '''
            }
        }

        stage('Create User') {
            steps {
                sh """
                ansible-playbook \
                -i inventory.ini \
                create_user.yml \
                -e "username=${params.USERNAME}"
                """
            }
        }
    }
}

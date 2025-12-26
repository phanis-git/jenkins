pipeline {
    // agent any
    // agent {
    //     node {
    //         label 'AGENT-1'
    //     }
    // }
    agent { label 'AGENT-1' }
     environment { 
        COURSE = 'Jenkins'
    }
    options {
        timeout(time: 10, unit: 'SECONDS') 
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Verify Agent') {
            steps {
                sh '''
                  echo "Node name: $NODE_NAME"
                  echo "Workspace: $WORKSPACE"
                  hostname
                  whoami
                '''
            }
        }
        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
        stage('Build') {
            steps{
                script {
                    sh """
                        echo "This is Building stage"
                        echo $COURSE
                        env
                        sleep 10
                    """
                }
            }
        }
        stage('Test') {
            steps{
                script {
                    sh """
                        echo "This is Testing stage"
                    """
                }
            }
        }
        stage('Deploy') {
            steps{
                script {
                    sh """
                        echo "This is Deploying stage"
                    """
                }
            }
        }
    }
    post {
        always {
            echo "This is execute always even the pipeline success or failure"
            cleanWs() 
        }
        aborted {
            echo "Pipeline is taken more than 10 seconds"
        }
    }
}
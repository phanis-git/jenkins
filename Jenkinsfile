pipeline {
    // agent any
    // agent {
    //     node {
    //         label 'AGENT-1'
    //     }
    // }
    agent { label 'AGENT-1' }
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
        stage('Build') {
            steps{
                echo "This is Building stage"
            }
        }
        stage('Test') {
            steps{
                echo "This is Testing stage"
            }
        }
        stage('Deploy') {
            steps{
                echo "This is Deploying stage"
            }
        }
    }
}
pipeline {
    agent any
    stages {
        stage ('clean') {
            steps {
                cleanWs()
                git url: 'https://github.com/agray998/jenkins-freestyle-project', branch: 'main'
            }
        }
        stage ('Run script') {
            steps {
                sh "sh run.sh"
            }
        }
        stage ('Generate artifacts') {
            steps {
                sh '''
                bash stage-2.sh
                '''
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '*.txt', followSymlinks: false
        }
    }
}
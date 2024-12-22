pipeline {
    agent any
    stages {
        stage('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
        failure {
        mail to: 'test.aqa4@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
       }
       success {
        mail to: 'test.aqa4@gmail.com',
             subject: "Successful Pipeline: ${currentBuild.fullDisplayName}",
             body: "All good with ${env.BUILD_URL}"
       }
    }
}

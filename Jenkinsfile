
pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                ech 'Hello World'
            }
        }

        stage('Run Script') {
            steps {
                sh '''
                    chmod +x hello.sh
                    ./hello.sh
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished (success, failure, or aborted).'
        }

        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
             mail to: 'ahmed.ishanab2@gmail.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something went wrong! Check the logs here: ${env.BUILD_URL}"
        }

        aborted {
            echo 'Pipeline was aborted!'
        }
    }
}

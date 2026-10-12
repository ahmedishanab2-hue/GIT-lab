
pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                echo 'Hello World'
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

    mail(
        to: 'ahmed.ishanab2@gmail.com',
        subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
        mimeType: 'text/html',
        body: """
            <html>
            <body>
                <h2 style="color: red;">Jenkins Pipeline Failed</h2>

                <p>Here is the pipeline report:</p>

                <table style="border-collapse: collapse; width: 100%;"
                       border="1" cellpadding="8">

                    <tr style="background-color: #333333; color: white;">
                        <th>Job</th>
                        <th>State</th>
                        <th>Cost</th>
                    </tr>

                    <tr>
                        <td>${env.JOB_NAME}</td>
                        <td style="color: red;">${currentBuild.currentResult}</td>
                        <td>$0.00</td>
                    </tr>

                </table>

                <p>
                    <a href="${env.BUILD_URL}">View Jenkins Build Logs</a>
                </p>
            </body>
            </html>
        """
    )
}

        aborted {
            echo 'Pipeline was aborted!'
        }
    }
}

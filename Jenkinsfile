pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo "Testing the application..."
                echo "Executing pipeline for branch ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Building the application..."
            }
        }

        stage('Deploy') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Deploying the application..."
            }
        }
    }

    post {
        success {
            script {
                def payload = [
                    content: "✅ Build SUCCESS on ${env.BRANCH_NAME}\n🔗 URL: ${env.BUILD_URL}"
                ]
                httpRequest(
                    httpMode: 'POST',
                    contentType: 'APPLICATION_JSON',
                    requestBody: groovy.json.JsonOutput.toJson(payload),
                    url: 'https://discordapp.com/api/webhooks/1425105978277498900/h3TP6MRKlZ_dnwnBO12Y6Yc85_jLpSUnNH1gZZc4etjxtECt_QVTIg8RlCSnL9ig7mxS'
                )
            }
        }

        failure {
            script {
                def payload = [
                    content: "❌ Build FAILED on ${env.BRANCH_NAME}\n🔗 URL: ${env.BUILD_URL}"
                ]
                httpRequest(
                    httpMode: 'POST',
                    contentType: 'APPLICATION_JSON',
                    requestBody: groovy.json.JsonOutput.toJson(payload),
                    url: 'https://discordapp.com/api/webhooks/1425105978277498900/h3TP6MRKlZ_dnwnBO12Y6Yc85_jLpSUnNH1gZZc4etjxtECt_QVTIg8RlCSnL9ig7mxS'
                )
            }
        }
    }
}

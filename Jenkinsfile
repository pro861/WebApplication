pipeline {
    agent any
   
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pro861/WebApplication.git'
            }
        }
        
        stage('Archive Artifactsssssss') {
            steps {
                archiveArtifacts artifacts: '**/bin/Release/**/*', fingerprint: true
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        failure {
            script {
                try {
                    slackSend channel: '#build-failures', color: 'danger', message: "Build failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
                } catch (Exception e) {
                    echo "Slack notification failed: ${e.message}"
                }
            }
        }
    }
}

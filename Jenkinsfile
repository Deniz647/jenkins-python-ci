pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh 'pytest tests'
            }
        }
        stage('Build') {
            steps {
                sh 'zip -r app.zip .'
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'app.zip', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build Success'
        }
        failure {
            echo 'Build fehlgeschlagen'
            // mail to: 'deniz-can96@hotmail.com.com',
            //      subject: "Build fehlgeschlagen: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            //      body: "Der Build ist fehlgeschlagen. Bitte prüfen."
        }
    }
}

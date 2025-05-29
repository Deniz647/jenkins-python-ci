pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'python3 -m unittest discover tests'
            }
        }

        stage('Build') {
            steps {
                sh 'zip -r app.zip . -x "*.git*" "*tests/*"'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'app.zip'
            }
        }
    }

    post {
        success {
            echo 'Build Success'
        }
        failure {
            mail to: 'entwickler@example.com',
                 subject: "Build fehlgeschlagen: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Der Build ist fehlgeschlagen. Bitte prüfen."
        }
    }
}




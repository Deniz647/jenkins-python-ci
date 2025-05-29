pipeline {
    agent {
        docker {
            image 'python:3.9'
            args '-u root:root'
        }
    }

    stages {
        stage('Test') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'pytest'
            }
        }
        stage('Build') {
            steps {
                sh 'zip -r app.zip .'
            }
        }
        stage('Artefakt') {
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
            echo 'Build failed, check logs.'
            // Mail kann problematisch sein, weil SMTP nicht konfiguriert ist
        }
    }
}




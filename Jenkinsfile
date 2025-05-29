pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'pip install -r requirements.txt'
                sh 'pytest'
            }
        }
    }

    post {
        always {
            mail to: 'deniz-can96@hotmail.com',
                 subject: "Jenkins Build ${currentBuild.fullDisplayName}",
                 body: "Build Status: ${currentBuild.currentResult}"
        }
    }
}





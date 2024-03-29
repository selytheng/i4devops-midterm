pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/selytheng/i4devops-midterm.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }

    post {
        always {
            junit 'build/reports/**/*.xml'
            archiveArtifacts 'build/libs/*.jar'
        }
        success {
            emailext body: 'Build successful',
                     subject: 'Build Success Notification',
                     to: '6b2d8e13764f87'
        }
        failure {
            emailext body: 'Build failed',
                     subject: 'Build Failure Notification',
                     to: '6b2d8e13764f87'
        }
    }
}

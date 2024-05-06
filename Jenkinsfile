pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('pmd') {
            steps {
                bat 'mvn pmd:pmd'
            }
        }
        stage('Test Report') {
            steps {
                bat 'mvn surefire-report:report --fail-never'
                bat 'mvn javadoc:doc --fail-never'
            }
        }
    }
    post{
        always {
            archiveArtifacts artifacts: '**/target/site/surefire-report.html', fingerprint: true
            archiveArtifacts artifacts: '**/target/site/pmd.html', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
       }
   }
}
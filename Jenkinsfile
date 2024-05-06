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
    }
}
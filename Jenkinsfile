pipeline {
    agent { node { label 'Agent-1' } } 
    stages {
        stage('Install dependencies') {
            steps {
                echo 'npm install'
            }
        }
        stage('unit test') {
            steps {
                echo 'unit testing is done here'
            }
        }
    }
}
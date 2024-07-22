pipeline {
    agent { node { label 'Agent-1' } } 
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('unit test') {
            steps {
                echo 'unit testing is done here'
            }
        }
        // stage('sonar scan') {
        //     steps {
        //         sh 'ls -ltr'
        //         sh 'sonar-scanner'
        // }
        // }
        stage('Build') {
            steps {
                sh 'ls -ltr'
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
        }
        }
        stage('Publish artifact') {
            steps {
                nexusArtifactUploader(
                nexusVersion: 'nexus3',
                protocol: 'http',
                nexusUrl: '54.196.75.145:8081/',
                groupId: 'com.roboshop',
                version: '1.0.0',
                repository: 'catalogue',
                credentialsId: 'nexus-auth',
                artifacts: [
                    [artifactId: 'catalogue',
                    classifier: '',
                    file: 'catalogue.zip',
                    type: 'zip']
                ]
                )
            }
        }
        stage('Deploy') {
            steps {
                echo 'deployment'
        }
        }
    }
    post{
        always{
            echo 'cleaning up workspace'
            //deleteDir()
        }
    }
}
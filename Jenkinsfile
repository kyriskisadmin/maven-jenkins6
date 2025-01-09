pipeline {
    agent any
    tools {
        maven 'maven3'
        jdk 'java17'
    }
    stages {
        stage('Download Code From Git') {
            steps {
                git branch: 'main', url: 'https://github.com/kyriskisadmin/maven-jenkins6.git'
            }
        }
        stage('Build Java Project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
		stage('Start Deploy project') {
            steps {
                build wait: false, job: 'dev-deploy-pipeline'
            }
        }
    }
}
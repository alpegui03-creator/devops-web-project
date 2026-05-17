pipeline {
    agent {
        node {
        label 'dockerhost-build-server'
        }
    }
    tools {
        maven 'maven-3.9.6'
    }
    stages {
        stage('Packaging') {
            steps {
                echo 'Packaging..'
                sh 'mvn clean package'
            }
        }
        stage('Copying war file') {
            steps {
                echo 'Copying war file..'
                sh 'mv target/*.war .'
            }
        }
        stage('cleanup') {
          steps {
            sh 'docker system prune -a --volumes --force --filter "label=devops-web-project-server"'

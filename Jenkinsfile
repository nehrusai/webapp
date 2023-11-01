pipeline {
    agent any

    stages {
        stage('stage1') {
            steps {
                echo 'git checkout'
                git 'https://github.com/sebsto/webapp.git'
            }
        }
        stage('stage2'){
            steps {
                echo 'mvn package'
                bat 'mvn clean install'  
            }
        }
        stage('stage3'){
            steps {
                echo 'mvn package'
                bat 'mvn package'  
            }
        }
        stage('stage4'){
            steps {
                echo 'deploy'
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://localhost:8085/')], contextPath: 'WebApp', war: '**/*.war'
            }
        }
    }
}


pipeline {
    agent { label 'linux' }
    tools {
      maven 'Maven-3.8.7'
    }
    stages {
        stage('Source') {
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'main',
                    url: 'https://github.com/Pathak-Akshay/jenkins_add_ssh_node1.git'
            }
        }
        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}/maven_project/test"){
                    sh 'mvn clean'
                }
            }
        }
        stage('Test') {
            steps {
                dir("${env.WORKSPACE}/maven_project/test"){
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            steps {
                dir("${env.WORKSPACE}/maven_project/test"){
                    sh 'mvn package -DskipTests'
                }
            }
        }
    }
}

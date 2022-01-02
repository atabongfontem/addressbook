pipeline {
    agent any
    stages {
        stage ('compilation') {
            steps {
                sh 'mvn -B compile'
            }
        }
        stage ('static code analysis') {
            steps {
                sh 'echo hello there. this  is static code analysis stub'
//                sh '/home/ubuntu/sonar-scanner-4.6.2.2472-linux/bin/sonar-scanner'
            }
        }
        stage ('package') {
            steps {
                sh 'mvn -B package'
            }
        }
        stage ('build and publish to dockerhub') {
            steps {
                sh 'sudo docker build -t atabongfontem/ab:v1 .'
                sh 'sudo docker push atabongfontem/ab:v1'
            }
        }
    }
    post {
        failure {
            sh 'echo the build failed'
        }
        success {
            sh 'echo the build is SUCCESSFULL'
        }
        always {
            sh 'echo the build as completed'
        }
    }
}

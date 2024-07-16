pipeline {
    agent any

    stages {
        stage('git') {
            steps {
               git branch: 'main', url: 'https://github.com/chandu2266/casino.git'
            }
        }
        stage ('buid') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tom', path: '', url: 'http://13.233.96.48:8080/')], contextPath: 'casino', war: '**/*.war'
            }
        }
        stage('triggers') {
            steps {
                 cron('H/2 * * * *')
            }
            
        }
    }
}

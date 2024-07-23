pipeline {
    agent any
    triggers {
        cron('H/2 * * * *')
    }
    stages {
        stage('git') {
            steps {
               git branch: 'main', url: 'https://github.com/chandu2266/casino.git'
            }
        }
        stage ('deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tom', path: 'chandu', url: 'http://3.108.220.205:8080/')], contextPath: 'casino', war: '**/*.war'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv(credentialsId: 'project-1token') {
                        sh 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
}

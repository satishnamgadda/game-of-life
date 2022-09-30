pipeline {
    agent { label 'JDK-11' }
    stages {
        stage('vcs') {
            steps {
                git branch: 'REL_INT_1.0', url: 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('build') {
            steps {
                sh '/usr/share/maven/bin/mvn package'
            }
        } 
        stage('archive artifacts') {
            steps {
                archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
            }
        } 
        stage('test results') {
            steps {
                junit '**/surefire-reports/*.xml'
            }
        }
    }
} 






pipeline {
    agent { label 'JDK11' }
    stages {
        stage('vcs') {
            steps {
                mail subject: "build started",
                     body: "build started",
                     to: "qtdevops@gmail.com"
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
        post {
            always {
                echo 'job completed'
                mail subject: "build completed",
                    body: "build completed",
                    to: "qtdevops@gmail.com"
            }
            failure {
                mail subject: "build failed",
                     body: "build failed",
                     to: "qtdevops@gmail.com"

            }
            success {
                 junit '**/surefire-reports/*.xml'

            }
        }        
    }
} 






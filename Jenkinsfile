pipeline {
    agent { label 'build' }
    stages {
        stage('vcs') {
            steps {
                git url: "https://github.com/satishnamgadda/game-of-life.git",
                    branch: "REL_INT_1.0"
            }
        }
        stage('buildstage') {
            steps {
                sh 'docker info'
                sh 'docker image build -t satish1990/gol:1.0 .'
            }
        }
        stage('push') {
            steps {
                sh 'docker image push satish1990/gol:1.0'
            }
        }
    }
}
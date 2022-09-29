node('JDK-11') {
    stage('vcs') {
        git branch: 'REL_INT_1.0', url: 'https://github.com/satishnamgadda/game-of-life.git'
    }
    stage("build") {
        sh '/usr/share/maven/bin/mvn package'
    }
    stage("archive artifacts") {
        archiveArtifacts artifacts: 'gameoflife-web/target/*.war', followSymlinks: false
    }
 stage("archive results") {
        junit '**/surefire-reports/*.xml'
    }
}






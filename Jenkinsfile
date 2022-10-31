pipeline {
    agent  { label 'JDK11' }   
    stages {
        stage('vcs') {
            steps {
                   mail subject: 'build started',
                     body: 'build started',
                     to: 'qtdevops@gmail.com'
                git branch: "REL_INT_1.0", url: 'https://github.com/satishnamgadda/game-of-life.git'
            }

        }
        stage('artifactory configuaration') {
            steps {
                rtMavenDeployer (
                   id : "MVN_DEFAULT",
                   releaseRepo : "goll-libs-release-local",
                   snapshotRepo : "goll-libs-snapshot-local",
                   serverId : "JFROG-GOL"
                )

            }
        }
        stage('Exec Maven') {
            steps {
                rtMavenRun(
                    tool : "mvn",
                    pom : "pom.xml",
                    goals : "clean install",
                    deployerId : "MVN_DEFAULT"
                )
          
            }
        }
 
        stage('publish build info') {
           steps {
               rtPublishBuildInfo(
                serverId : "JFROG-GOL"
               )
           }
        }
    }
}
    

pipeline(){
    agent(){
        stages{
            stage('Version Control'){
                steps{
                    git url: 'https://github.com/SGDevopsTrg/game-of-life.git',
                    branch: 'jenkinsScriptedPipeline',
                    poll: false
                }
            }
            stage('Create a Build'){
                steps{
                    sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package' 
                }
            }
            stage('Archive the Artifects'){
                steps{
                    archiveArtifacts onlyIfSuccessful: true,
                                        artifacts: '**/target/gameoflife.war',
                                        allowEmptyArchive: true
                }
            }
            stage('Archive the Artifects'){
                steps{
                    junit testResults: '**/surefire-reports/TEST-*.xml',
                    allowEmptyArchive: false
                }
            }
        }
    }
}
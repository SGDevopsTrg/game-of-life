pipeline{
    agent none
    stages{
        stage('Version Control'){
            steps{
                git url: 'https://github.com/SGDevopsTrg/game-of-life.git',
                branch: 'jenkinsScriptedPipeline',
                poll: false
            }
        }
        stage('Create a Build'){
            environment{
                PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH"
            }
            steps{
                sh 'mvn package'
            }
        }
        stage('Archive the Artifects'){
            steps{
                archiveArtifacts onlyIfSuccessful: true,
                                    artifacts: '**/target/gameoflife.war',
                                    allowEmptyArchive: true
            }
        }
    }
}
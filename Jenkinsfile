pipeline{
    agent {label 'MAVEN_JDK8'}
    stages{
        stage('Version Control'){
            steps{
                git url: 'https://github.com/SGDevopsTrg/game-of-life.git',
                    branch: 'jenkinsDeclarativePipeline',
                    poll: false
            }
        }
        stage('Create a Build'){
            tools{
                jdk 'JDK_8_UBUNTU'
            }
            steps{
                sh 'mvn package'
            }
        }
        stage('Archive the Artifects'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true,
                                 allowEmptyArchive: true
            }
        }
        stage('Show the TestResults'){
            junit testResults: '**/surefire-reports/TEST-*.xml',
            allowEmptyArchive: false
        }
    }
}
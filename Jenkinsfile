pipeline{
  agent any
  options{
    buildDiscarder(logRotator(daysToKeepStr: '5', numToKeepStr: '5'))
    timeout(time:5, unit:'HOURS')
    timestamps()
  }

  stages{
    stage('Requirements'){
      steps{
        sh('chmod +x ./algorithm.sh')
      }
    }

    stage('Build') {
      steps{
        sh('./algorithm.sh')
        archiveArtifacts allowEmptyArchive: true,
                    artifacts: '*.txt',
                    fingerprint: true,
                    onlyIfSuccessful: true
        
      }
    }
  }
}

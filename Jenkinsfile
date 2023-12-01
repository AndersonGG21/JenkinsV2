pipeline {
  agent any
  stages {
    stage('Branch indexing: abort') {
        when {
            allOf {
                triggeredBy cause: "BranchIndexingCause"
                not {
                    changeRequest()
                }
            }
        }
        steps {
            script {
                echo "Branch discovered by branch indexing"
                currentBuild.result = 'SUCCESS'
                error "Caught branch indexing..."
            }
        }
    }
  }
}
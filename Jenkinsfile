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
            }
        }
    }

    stage('Build') {
      steps {
        echo 'Building'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing'
      }
    }

    stage('Deploy') {
      when {
           branch 'main'
      }
      steps {
        echo 'Deploying'
      }
    }

  }
}
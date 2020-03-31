pipeline{
    agent any 
    tools { maven "MAVEN_HOME" }
    parameters{
        gitParameter branchFilter: 'origin/(.*)', defaultValue: 'origin/devlop', name: 'BRANCH', type: 'PT_BRANCH'
        gitParameter name: 'TAG',type: 'PT_TAG', selectedValue: 'NONE'
    }
    stages{
        stage ('dev') {
            when { 
                expression {BRANCH == 'origin/devlop' || BRANCH == 'devlop'  }
            }
            steps{
                sh 'mvn validate'
                sh 'mvn compile'
                sh 'mvn test'
               
            }
        }

        stage ('QA'){
            when {
                expression { BRANCH == 'origin/release'  || BRANCH == 'release' }
            }
            steps{
                   sh 'mvn install' 
                   echo '=====TAG======='
            }
        }
        
        
    }
}

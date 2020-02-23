pipeline{
    agent{
        label 'maven'
    }
    stages{
        stage ('build master'){
            when {
                branch 'master'
            }
            tools{
                maven 'MAVEN_HOME'
                jdk 'JAVA_HOME'
            }
            steps{
                timestamps{
                 echo '========master======='
                 sh 'mvn install'
                 sh 'mvn versions:set -Dnewversion=2.0.1
                }
               
            }
        }
        stage ('build release'){
            when {
                branch 'release'
            }
            tools{
                maven 'MAVEN_HOME'
            }
            steps{
                echo '======release========='
                sh 'mvn install'
            }
        }
    }
}

pipeline{
    agent any
    Tool{
        jdk 'java8'
        maven 'maven'
    }
    stages{
        stage("Initiliszing") {
            steps{
                echo "This is Initializing stage"
            }
        }
        stage("Build"){
            steps{
                echo "This is Build stage"
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
            }
            post{
                success{
                    echo "Displaying Archive artifacts results"
                    archiveArtifacts '**/*.war'
                    echo "Displaying Junit result"
                    junit '**/surefire-reports/*.xml'
                    echo "Displaying checkstyle result"
                    checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploy stage"
            }
        }
        
        

    }
}
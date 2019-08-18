pipeline{
    agent any
    tools{
        maven 'Maven3'
        jdk 'Java 8'

    }
    stages{
        stage('init'){
            steps{
                echo"This is initializing stage"
            }
        }
        stage('Build'){
            steps{
                echo"This is Build stage"
                sh label: '', script: 'mvn clean package checkstyle:checkstyle'
                
            }
            post{
                success{
                        echo"post success script start executing..."
                        checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                        junit '**/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy'){
            steps{
                echo"This is Deployment stage"
                build 'deploy to tomcat'
            }
        }
    }
}
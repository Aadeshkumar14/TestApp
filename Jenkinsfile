pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat7(credentialsId: 'tom', path: '', url: 'http://34.212.136.85:8088')], contextPath: null, war: '**/*.war'
                echo "Deployment.."
            }
        }
    }
}

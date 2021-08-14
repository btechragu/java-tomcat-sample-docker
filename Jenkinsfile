pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Create Docker File'){
            steps{
               sh "docker build -t tomcatsamplewebapp:${env.BUILD_ID} ."
            }
            
        }
    }
}
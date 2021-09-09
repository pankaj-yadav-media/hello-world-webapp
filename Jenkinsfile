pipeline {
    agent any


    tools {
        dockerTool 'docker'
        jdk 'jdk-11'
    }


    stages {
        stage('Git Clone') {
            steps {
               git branch: 'testing', changelog: false, poll: false, url: 'https://github.com/pankaj-yadav-media/hello-world-webapp.git'
            }
        }

        stage('Deploy'){
            steps{
                // script {
                //     // def image = docker.build("pankajyadav404/training:latest")
                    
                //     // withDockerRegistry(credentialsId: 'docker-hub-credentials', toolName: 'docker') {
                //     //     def image = docker.build("pankajyadav404/training:latest")
                //     //     image.push()
                //     // }
                    
                // }

                echo "Done."
            }
    }

        stage('SonarQube analysis') {
            steps{
                    script{

                        def scannerHome = tool 'sonar_scanner';
                        
                        withSonarQubeEnv(installationName: 'SonarQube', credentialsId: 'temp-user-secret') { // If you have configured more than one global server connection, you can specify its name
                           sh "${scannerHome}/bin/sonar-scanner"
                        
                        }
                    }    
            }   
        }

        stage("Quality Gate"){
            steps{
                script{
                    timeout(time: 5, unit: 'MINUTES') { // Just in case something goes wrong, pipeline will be killed after a timeout
                    def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"
                        }
                    }   
                }
             }
        }
    }
}
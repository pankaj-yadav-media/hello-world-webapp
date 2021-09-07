pipeline {
    agent any


    tools {
        dockerTool 'docker'
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
                    
                        withSonarQubeEnv('sonar_scanner') { // If you have configured more than one global server connection, you can specify its name
                            sh "${scannerHome}/bin/sonar-scanner"
                        }
                    }
                    
            }
        }
    }
}
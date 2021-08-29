pipeline {
    agent any


    tools {
        dockerTool 'docker'
    }


    stages {
        stage('Git Clone') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/pankaj-yadav-media/hello-world-webapp'
            }
        }

    stage('Deploy'){
        steps{
            script {
                
                withDockerRegistry(credentialsId: 'docker-hub-credentials', toolName: 'docker') {
                    def image = docker.build("pankajyadav404/training:latest")
                    image.push()
                }
                
            }

            echo "Done."
        }
    }
    }
}
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
            script {
                def image = docker.build("pankajyadav404/training:latest")
                
                // withDockerRegistry(credentialsId: 'docker-hub-credentials', toolName: 'docker') {
                //     def image = docker.build("pankajyadav404/training:latest")
                //     image.push()
                // }
                
            }

            echo "Done."
        }
    }
    }
}
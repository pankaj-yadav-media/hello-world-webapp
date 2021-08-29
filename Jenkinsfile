pipeline {
    agent any


    stages {
        stage('Git Clone') {
            steps {
                git changelog: false, poll: false, url: 'https://github.com/pankaj-yadav-media/hello-world-webapp'
            }
        }


    stage('Build') {
        steps{
            sh "python -m install pip"
            sh "pip install -r requirements.txt"
            sh "gunicorn app:app"
        }
    }


    stage('Deploy'){
        steps{
            echo "Deploying"
        }
    }
    }
}
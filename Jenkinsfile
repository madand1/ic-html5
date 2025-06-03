pipeline {
    agent {
        docker {
            image 'josedom24/debian-npm'
            args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'master', url: 'https://github.com/madand1/ic-html5.git'
            }
        }
        
        stage('Install surge') {
            steps {
                sh 'npm install -g surge'
            }
        }
        
        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'SURGE_TOKEN', variable: 'TOKEN')]) {
                    sh 'surge ./_build/ asirandy-practica.surge.sh --token $TOKEN'
                }
            }
        }
    }
}

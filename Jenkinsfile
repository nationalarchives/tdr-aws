pipeline {
    agent {
        docker {
            image 'python:3.6'
            args '-u root:root'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                checkout(scm)
            }
        }
        
        stage('Install') {
            steps {
                sh('pip install -r requirements.txt')
            }
        }

        stage('Run checks') {
            steps {
                sh('python -B -m xmlrunner discover tests --output-file junit.xml')
            }
        }
    }
    post {
        always {
            junit 'junit.xml'
        }
    }
}
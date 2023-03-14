pipeline {
    agent any
    stages {
        stage('Build Frontend Web') {
            steps {
                echo 'Building Frontend Angular'
                dir ('Angular6BaseCli/'){
                    bat 'npm install'
                    bat 'npm run build'
                }
            }
        }
    }
    post { 
        always { 
            deleteDir()
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            sh 'docker-compose down'
            echo 'I am unstable :/'
        }
        failure {
            sh 'docker-compose down'
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
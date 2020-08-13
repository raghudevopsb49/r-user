pipeline {
    
    agent any
    
    stages { 
        stage('NPM Install') {
            steps {
                sh label: '', script: '''
                  npm install
                '''
            }
        }

        stage('Archive') {
            steps {
                sh 'tar -czf user.tgz node_modules user.js'
            }
        }

    }
    
}